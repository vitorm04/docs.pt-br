---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 107936aa969690d0cc9fd4a2605cfceea31eeca8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161407"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a>BC31194: o valor do tipo ' type1 ' não pode ser convertido em ' type2 '

O valor do tipo ' type1 ' não pode ser convertido em ' type2 '. Você pode usar a propriedade ' value ' para obter o valor da cadeia de caracteres do primeiro elemento de ' \<parentElement> '.

 Foi feita uma tentativa de converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.

 **ID do erro:** BC31194

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Use a `Value` Propriedade do literal XML para referenciar seu valor como um `String` . Use a `CType` função, outra função de conversão de tipo ou a <xref:System.Convert> classe para converter o valor como o tipo especificado.

## <a name="see-also"></a>Veja também

- <xref:System.Convert>
- [Funções de conversão do tipo](../functions/type-conversion-functions.md)
- [Literais XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
