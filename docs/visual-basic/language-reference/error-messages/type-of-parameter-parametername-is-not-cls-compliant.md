---
title: "Tipo de parâmetro &quot;&lt;parametername&gt;&quot; não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
dev_langs:
- VB
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
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
ms.openlocfilehash: 75891a7268489b69e8d0c1bf91570a67fc004c6b
ms.lasthandoff: 03/13/2017

---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>Tipo de parâmetro '&lt;parametername&gt;' não é compatível com CLS
Um procedimento está marcado como `<CLSCompliant(True)>` mas declara um parâmetro com um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.  
  
 Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele deve usar somente tipos compatíveis com CLS. Isso se aplica os tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.  
  
 O seguinte [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute>para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade.</xref:System.CLSCompliantAttribute> Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute>a um elemento, ele é considerado incompatível.</xref:System.CLSCompliantAttribute>  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40028  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o procedimento deve aceitar um parâmetro desse tipo específico, remova o <xref:System.CLSCompliantAttribute>.</xref:System.CLSCompliantAttribute> O procedimento não pode ser compatível com CLS.  
  
-   Se o procedimento deve ser compatível com CLS, altere o tipo do parâmetro para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar do intervalo de valor acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Por exemplo, `int` é geralmente 16 bits em outros ambientes. Se você estiver retornando um inteiro de 16 bits de um componente, declare-o como `Short` em vez de `Integer` em gerenciado [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
