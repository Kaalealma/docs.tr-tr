---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: d71e3679f4bf395b240c330fc573d6f613d1be07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Üyelik sağlayıcısı sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kullanıcıların benzersiz bir kullanıcı adı ve parola birleşimlerini oluşturmasına izin Web siteleri oluşturmak için geliştiriciler. Bu özelliği sayesinde, herhangi bir kullanıcı sitesi olan bir hesap oluşturun ve site ve hizmetlerini özel erişim için oturum açın. Kullanıcıların bir Windows etki alanında hesaplarına sahip olmasını gerektiren Windows güvenliği aksine budur. Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) sağlayan herhangi bir kullanıcı site ve hizmetlerini kullanabilirsiniz.  
  
 Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Kullanma hakkında bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcı özelliği, bkz: [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanma üyelik özellik gerektirir. Özelliği de parolalarını unutmuş olan tüm kullanıcılar ile bir soru sormak için yöntemler içerir.  
  
 Windows Communication Foundation (WCF) geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilir. Bir WCF uygulamaya tümleştirildiğinde, kullanıcıların bir kullanıcı adı/parola birleşimini WCF istemci uygulaması için sağlamanız gerekir. WCF hizmetine veri aktarmak için kullanıcı adı/parola kimlik bilgileri gibi destekleyen bir bağlama kullanmak <xref:System.ServiceModel.WSHttpBinding> (yapılandırma, [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) ve istemci kimlik bilgisi türü olarakayarlayın`UserName`. Hizmeti, WCF güvenlik kullanıcı adı ve parolaya göre kullanıcının kimliğini doğrular ve ayrıca tarafından belirtilen rol atar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol.  
  
> [!NOTE]
>  WCF veritabanı kullanıcı adı/parola birleşimleri ile veya diğer kullanıcı bilgilerini doldurmak için yöntem sağlamaz.  
  
### <a name="to-configure-the-membership-provider"></a>Üyelik sağlayıcısı yapılandırmak için  
  
1.  Web.config dosyasındaki altında <`system.web`> öğesini oluşturmak bir <`membership`> öğesi.  
  
2.  Altında `<membership>` öğesini oluşturmak bir `<providers>` öğesi.  
  
3.  Alt öğesi olarak <`providers`> öğesi ekleme bir `<clear />` sağlayıcıları koleksiyonu temizlemek için öğesi.  
  
4.  Altında `<clear />` öğesini oluşturmak bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, ve `passwordFormat`. `name` Özniteliği kullanılır daha sonra yapılandırma dosyasındaki bir değer olarak. Aşağıdaki örnek, ayarlar `SqlMembershipProvider`.  
  
     Aşağıdaki örnek yapılandırma bölümü gösterir.  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Kullanıcı adı/parola birleşimini kabul etmek için hizmet güvenliği yapılandırmak için  
  
1.  Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
2.  Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bağlamaları bölümüne. Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Ayarlama `mode` özniteliği `<security>` öğesine `Message`.  
  
4.  Ayarlama `clientCredentialType` özniteliği <`message`> öğesine `UserName`. Bu, bir kullanıcı adı/parola çifti istemcinin kimlik bilgisi olarak kullanılacak belirtir.  
  
     Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Bir hizmeti üyelik sağlayıcıyı kullanacak şekilde yapılandırmak için  
  
1.  Alt öğesi olarak `<system.serviceModel>` öğesi ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi  
  
2.  Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.  
  
3.  Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` öznitelik için uygun bir değer.  
  
4.  Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için <`behavior`> öğesi.  
  
5.  Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için `<serviceCredentials>` öğesi.  
  
6.  Ayarlama `userNamePasswordValidationMode` özniteliğini `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, WCF kullanan Windows kimlik doğrulaması yerine [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.  
  
7.  Ayarlama `membershipProviderName` (sağlayıcıyı bu konunun ilk yordamda eklerken belirtilir) sağlayıcısının adı özniteliği. Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ASP üyelik özelliğini kullanan bir hizmet yapılandırmasını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Üyelik ve Rol Sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
