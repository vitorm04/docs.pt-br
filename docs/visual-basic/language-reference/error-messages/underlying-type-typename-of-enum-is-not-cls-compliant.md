---
title: "Tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
dev_langs:
- VB
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 51f9c520922260f6d38cf170f46f9c4d88ed4028
ms.lasthandoff: 03/13/2017

---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS
O tipo de dados especificado para essa enumeração não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS). Isso não é um erro no seu componente, pois o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suporte para este tipo de dados. No entanto, outro componente escrito em estritamente código compatível com CLS pode não oferecer suporte a esse tipo de dados. Esse componente não poderá interagir com êxito com seu componente.  
  
 O seguinte [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40032  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se seu componente interfaces somente com outras [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] componentes ou não não interface com quaisquer outros componentes, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente não gravado para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], você poderá determinar, através de reflexão ou da documentação, se ele suporta esse tipo de dados. Se isso acontecer, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar do intervalo de valor acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Por exemplo, `uint` é geralmente 16 bits em outros ambientes. Se você estiver passando um argumento de 16 bits para tal um componente, declare-o como `UShort` em vez de `UInteger` em gerenciado [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [Reflexão](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Reflexão](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)   
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
