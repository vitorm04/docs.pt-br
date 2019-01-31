---
title: O nome <namespacename> no namespace raiz <fullnamespacename> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: c5afdcc98b7acb1927c9b0735a69fbe64c3d8e60
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268710"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Nome da \<namespacename > no namespace raiz \<fullnamespacename > não é compatível com CLS
Um assembly é marcado como `<CLSCompliant(True)>`, mas um elemento do nome do namespace raiz começa com um sublinhado (`_`).  
  
 Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40039  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de conformidade com CLS, altere o nome do namespace raiz para que nenhum de seus elementos começa com um sublinhado.  
  
-   Se você precisar que o nome do namespace permanecem inalterados, em seguida, remova os <xref:System.CLSCompliantAttribute> do assembly ou marcá-la como `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

