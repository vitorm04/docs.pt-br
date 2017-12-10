---
title: "Tipo de retorno de função &#39; &lt;procedurename&gt;&#39; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords: BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14adc6f8f2d89713bd681a1d55e4801b930cf642
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a>Tipo de retorno de função &#39; &lt;procedurename&gt;&#39; não é compatível com CLS
Um `Function` procedimento está marcado como `<CLSCompliant(True)>` , mas retorna um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.  
  
 Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS. Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.  
  
 O seguinte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40027  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o `Function` procedimento deve retornar esse tipo específico, remova o <xref:System.CLSCompliantAttribute>. O procedimento não pode ser compatível com CLS.  
  
-   Se o `Function` procedimento deve ser compatível com CLS, altere o tipo de retorno para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `int` é geralmente 16 bits em outros ambientes. Se você estiver retornando um inteiro de 16 bits para tal componente, declare-o como `Short` em vez de `Integer` em gerenciado [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [\<PAVE sobre > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
