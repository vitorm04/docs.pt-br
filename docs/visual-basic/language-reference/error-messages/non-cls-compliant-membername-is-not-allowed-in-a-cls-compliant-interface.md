---
title: <membername> não compatível com CLS não é permitido em uma interface compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: aa7944e90857436553435ce783c0820770496a49
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159983"
---
# <a name="bc40033-non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>BC40033: \<membername> não é permitido compatível com CLS em uma interface em conformidade com CLS

Uma propriedade, um procedimento ou um evento em uma interface é marcado como `<CLSCompliant(True)>` quando a própria interface está marcada como `<CLSCompliant(False)>` ou não está marcada.

 Para que uma interface seja compatível com a [independência de idioma e os componentes de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS), todos os seus membros devem estar em conformidade.

 Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.

 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.

 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID do erro:** BC40033

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Se você precisar de conformidade com CLS e tiver controle sobre o código-fonte da interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros estiverem em conformidade.

- Se você precisar de conformidade com CLS e não tiver controle sobre o código-fonte da interface, ou se ele não estiver qualificado para ser compatível, defina esse membro em uma interface diferente.

- Se você precisar que esse membro permaneça em sua interface atual, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque-o como `<CLSCompliant(False)>` .

## <a name="see-also"></a>Veja também

- [Instrução Interface](../statements/interface-statement.md)
