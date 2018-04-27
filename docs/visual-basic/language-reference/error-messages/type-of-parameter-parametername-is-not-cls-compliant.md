---
title: Tipo de parâmetro &#39; &lt;parametername&gt; &#39; não é compatível com CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d34de9e5914b02a0e878b87e786b81a5940a6d85
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>Tipo de parâmetro &#39; &lt;parametername&gt; &#39; não é compatível com CLS
Um procedimento está marcado como `<CLSCompliant(True)>` mas declara um parâmetro com um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.  
  
 Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS. Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40028  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o procedimento deve ter um parâmetro deste tipo específico, remova o <xref:System.CLSCompliantAttribute>. O procedimento não pode ser compatível com CLS.  
  
-   Se o procedimento deve ser compatível com CLS, altere o tipo do parâmetro para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `int` é geralmente 16 bits em outros ambientes. Se você estiver retornando um inteiro de 16 bits de um componente, declare-o como `Short` em vez de `Integer` no seu código Visual Basic gerenciado.