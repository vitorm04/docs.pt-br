---
title: O tipo de membro '<membername>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590678"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>Tipo de membro '\<membername >' não é compatível com CLS
O tipo de dados especificado para esse membro não é parte do [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS). Isso não é um erro no seu componente, porque o .NET Framework e Visual Basic dá suporte a esse tipo de dados. No entanto, outro componente escrito em estritamente código compatível com CLS pode não dar suporte a esse tipo de dados. Esse componente não pode ser capaz de interagir com êxito com seu componente.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
- [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se seu componente interage apenas com outros componentes do .NET Framework ou não estabelece uma interface com quaisquer outros componentes, você não precisará alterar nada.  
  
- Se você estiver fazendo interface com um componente não escrito para o .NET Framework, você poderá determinar, por meio de reflexão ou da documentação, se ele dá suporte a esse tipo de dados. Se isso acontecer, você não precisará alterar nada.  
  
- Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
- Se você estiver fazendo interface com objetos de automação ou COM, lembre-se de que alguns tipos têm larguras de dados diferente do que no .NET Framework. Por exemplo, `uint` geralmente é 16 bits em outros ambientes. Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` no seu código gerenciado do Visual Basic.  
  
## <a name="see-also"></a>Consulte também

- [Reflexão](../../../framework/reflection-and-codedom/reflection.md)
