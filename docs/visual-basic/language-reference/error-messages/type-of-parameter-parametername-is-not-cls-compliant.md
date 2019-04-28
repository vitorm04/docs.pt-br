---
title: O tipo de parâmetro '<parametername>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: e0852536a86dd415334f95a47ceb800ed2c591ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924014"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a>Tipo de parâmetro '\<parametername >' não é compatível com CLS
Um procedimento é marcado como `<CLSCompliant(True)>` mas declara um parâmetro com um tipo que está marcado como `<CLSCompliant(False)>`, não está marcada ou não se qualifica porque ele é um tipo incompatível.  
  
 Para obter um procedimento para estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS. Isso se aplica os tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
- [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40028  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se o procedimento deve levar um parâmetro desse tipo específico, remova o <xref:System.CLSCompliantAttribute>. O procedimento não pode ser compatível com CLS.  
  
- Se o procedimento deve ser compatível com CLS, altere o tipo desse parâmetro para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
- Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Por exemplo, `int` geralmente é 16 bits em outros ambientes. Se você estiver retornando um inteiro de 16 bits de tal componente, declare-o como `Short` em vez de `Integer` no seu código gerenciado do Visual Basic.