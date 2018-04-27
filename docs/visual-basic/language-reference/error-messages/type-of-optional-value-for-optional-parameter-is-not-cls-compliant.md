---
title: Tipo de valor opcional para parâmetro opcional &lt;parametername&gt; não é compatível com CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08457b5234b98cdff6fb3286b3442a6bd0155a37
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>Tipo de valor opcional para parâmetro opcional &lt;parametername&gt; não é compatível com CLS
Um procedimento está marcado como `<CLSCompliant(True)>` mas declara um [opcional](../../../visual-basic/language-reference/modifiers/optional.md) parâmetro com valor padrão de um tipo incompatível.  
  
 Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS. Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais. Ela também se aplica aos valores padrão de parâmetros opcionais.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40042  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o parâmetro opcional deve ter um valor padrão desse tipo específico, remova <xref:System.CLSCompliantAttribute>. O procedimento não pode ser compatível com CLS.  
  
-   Se o procedimento deve ser compatível com CLS, altere o tipo de valor padrão para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `int` é geralmente 16 bits em outros ambientes. Se você estiver retornando um inteiro de 16 bits de um componente, declare-o como `Short` em vez de `Integer` no seu código Visual Basic gerenciado.