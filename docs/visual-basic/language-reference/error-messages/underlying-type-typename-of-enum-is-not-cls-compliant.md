---
title: "O tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e054f8d992154f66ab1d48a477a7e04900aa5b4d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>O tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS
O tipo de dados especificado para essa enumeração não é parte do [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS). Isso não é um erro no seu componente, porque o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suporte para esse tipo de dados. No entanto, outro componente escrito em estritamente código compatível com CLS não pode oferecer suporte a esse tipo de dados. Esse componente não poderá interagir com êxito com seu componente.  
  
 O seguinte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40032  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o seu componente interfaces somente com outras [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] componentes ou não não interface com outros componentes, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente não gravado para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], você poderá determinar, através de reflexão ou da documentação, se ele dá suporte a esse tipo de dados. Em caso afirmativo, você não precisa alterar nada.  
  
-   Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `uint` é geralmente 16 bits em outros ambientes. Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` em gerenciado [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [Reflexão (Visual Basic)](../../programming-guide/concepts/reflection.md)  
 [Reflexão](../../../framework/reflection-and-codedom/reflection.md)  
 
