---
title: Bitwise İşleçleri (F#)
description: 'F # programlama dili kullanılabilen bit düzeyinde işleçler hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: bc653ae7ff6dd6bc2c269aaba344f073df1fb708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bitwise-operators"></a>Bitwise İşleçleri

Bu konu, F # dilinde kullanılabilir bit düzeyinde işleçler açıklar.

## <a name="summary-of-bitwise-operators"></a>Bit düzeyinde işleçler özeti
Aşağıdaki tabloda, F # dilinde sarmalanmamış tam sayı türleri için desteklenen bit düzeyinde işleçler açıklanmaktadır.

|İşleç|Notlar|
|--------|-----|
|`&&&`|Bit düzeyinde AND işleci. Her iki kaynak işlenen karşılık gelen bitleri 1 olan yalnızca ve yalnızca, BITS sonuç 1 değerine sahip.|
|<code>&#124;&#124;&#124;</code>|Bit düzeyinde OR işleci. BITS sonuç varsa 1 değerini ya da kaynak karşılık gelen bitleri işlenenler 1 olan.|
|`^^^`|Bit düzeyinde özel OR işleci. Kaynak işlenen bit eşit olmayan değerleri varsa ve yalnızca varsa BITS sonuç değeri 1 gerekir.|
|`~~~`|Bit düzeyinde değilleme işleci. Bu birli işleç ve bir sonuç kaynak işlenen tüm 0 bit 1 BITS dönüştürülür ve tüm 1 BITS 0 BITS dönüştürülür üretir.|
|`<<<`|Bit düzeyinde sola kaydırma işleci. İkinci işlenen bit sayısına göre sola bit ilk terimiyle gölgeye sonucudur. En önemli konumu gölgeye BITS en az önemli konumun döndürülemez. En az önemli BITS sıfırlarla. İkinci bağımsız değişken türü `int32`.|
|`>>>`|Bitwise sağ kaydırma işleci. İkinci işlenen bit sayısına göre sağa gölgeye BITS ilk terimiyle sonucudur. En az önemli konumu gölgeye BITS en önemli konumun döndürülemez. İmzasız türler için en önemli BITS sıfırlarla. İmzalı türler için en önemli BITS olanları ile doldurulur. İkinci bağımsız değişken türü `int32`.|

Bit düzeyinde işleçler ile aşağıdaki türleri kullanılabilir: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, ve `unativeint`.

## <a name="see-also"></a>Ayrıca Bkz.
[Simge ve İşleç Başvurusu](index.md)

[Aritmetik İşleçler](arithmetic-operators.md)

[Boole İşleçleri](boolean-operators.md)

