---
title: Tipo de membro &#39; &lt;membername&gt; &#39; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 5735b5104884a702a649a029116be7446424ec67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a>Tipo de membro &#39; &lt;membername&gt; &#39; não é compatível com CLS
O tipo de dados especificado para este membro não é parte do [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS). Isso não é um erro no seu componente, porque o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e Visual Basic oferecem suporte a esse tipo de dados. No entanto, outro componente escrito em estritamente código compatível com CLS não pode oferecer suporte a esse tipo de dados. Esse componente não poderá interagir com êxito com seu componente.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o seu componente interfaces somente com outras [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] componentes ou não não interface com outros componentes, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente não gravado para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], você poderá determinar, através de reflexão ou da documentação, se ele dá suporte a esse tipo de dados. Em caso afirmativo, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `uint` é geralmente 16 bits em outros ambientes. Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` no seu código Visual Basic gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Reflexão](../../../framework/reflection-and-codedom/reflection.md)  
 
