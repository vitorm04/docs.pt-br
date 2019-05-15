---
title: O tipo subjacente <typename> de Enum não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 7d4566637da74726867c55ddf89b965d055e5d14
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589923"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a>O tipo subjacente \<typename > de Enum não é compatível com CLS
O tipo de dados especificado para essa enumeração não é parte do [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS). Isso não é um erro no seu componente, porque o .NET Framework e Visual Basic dá suporte a esse tipo de dados. No entanto, outro componente escrito em estritamente código compatível com CLS pode não dar suporte a esse tipo de dados. Esse componente não pode ser capaz de interagir com êxito com seu componente.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
- [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40032  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se seu componente interage apenas com outros componentes do .NET Framework ou não estabelece uma interface com quaisquer outros componentes, você não precisará alterar nada.  
  
- Se você estiver fazendo interface com um componente não escrito para o .NET Framework, você poderá determinar, por meio de reflexão ou da documentação, se ele dá suporte a esse tipo de dados. Se isso acontecer, você não precisará alterar nada.  
  
- Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
- Se você estiver fazendo interface com objetos de automação ou COM, lembre-se de que alguns tipos têm larguras de dados diferente do que no .NET Framework. Por exemplo, `uint` geralmente é 16 bits em outros ambientes. Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` no seu código gerenciado do Visual Basic.  
  
## <a name="see-also"></a>Consulte também

- [Reflexão (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [Reflexão](../../../framework/reflection-and-codedom/reflection.md)
