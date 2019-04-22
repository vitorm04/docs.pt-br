---
title: Escopo no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 6139af65958cefe43578f436204fa6836a71de0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823539"
---
# <a name="scope-in-visual-basic"></a>Escopo no Visual Basic
O *escopo* de um elemento declarado é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome ou tornando-os disponíveis por meio de uma [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Um elemento pode ter escopo em um dos seguintes níveis:  
  
|Nível|Descrição|  
|-----------|-----------------|  
|Escopo de bloco|Disponível somente dentro do código de bloco no qual ele é declarado|  
|Escopo do procedimento|Disponível para todo o código dentro do procedimento no qual ela é declarada|  
|Escopo de módulo|Disponível para todo o código dentro do módulo, classe ou estrutura na qual ele está declarado|  
|Escopo de Namespace|Disponível para todo o código no namespace no qual ela é declarada|  
  
 Esses níveis de progresso de escopo de menor (bloco) para o mais amplo (namespace), onde *menor escopo* significa o menor conjunto de código que pode se referir ao elemento sem qualificação. Para obter mais informações, consulte "Níveis de escopo" nesta página.  
  
## <a name="specifying-scope-and-defining-variables"></a>Especificar o escopo e definir variáveis  
 Especifique o escopo de um elemento quando você declará-la. O escopo pode depender dos seguintes fatores:  
  
-   A região (bloco, procedimento, módulo, classe ou estrutura) em que você declara o elemento  
  
-   O namespace que contém a declaração do elemento  
  
-   O nível de acesso que você declarar para o elemento  
  
 Tenha cuidado ao definir variáveis com o mesmo nome mas com escopo diferente, porque isso pode levar a resultados inesperados. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Níveis de escopo  
 Um elemento de programação está disponível em toda a região na qual você declará-la. Todo o código na mesma região pode se referir ao elemento sem qualificar seu nome.  
  
### <a name="block-scope"></a>Escopo de bloco  
 Um bloco é um conjunto de instruções entre Iniciando e encerrando instruções de declaração, como o seguinte:  
  
-   `Do` e `Loop`  
  
-   `For` [`Each`] e `Next`  
  
-   `If` e `End If`  
  
-   `Select` e `End Select`  
  
-   `SyncLock` e `End SyncLock`  
  
-   `Try` e `End Try`  
  
-   `While` e `End While`  
  
-   `With` e `End With`  
  
 Se você declarar uma variável dentro de um bloco, você pode usá-lo apenas dentro desse bloco. No exemplo a seguir, o escopo da variável de inteiro `cube` é o bloco entre `If` e `End If`, e você não pode consultar `cube` quando a execução passa para fora do bloco.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Mesmo se o escopo de uma variável é limitado a um bloco, seu tempo de vida ainda é que todo o procedimento. Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco reterá seu valor anterior. Para evitar resultados inesperados, nesse caso, é prudente inicializar variáveis de bloco no início do bloco.  
  
### <a name="procedure-scope"></a>Escopo do procedimento  
 Um elemento declarado dentro de um procedimento não está disponível fora desse procedimento. Somente o procedimento que contém a declaração pode usá-lo. Variáveis com esse nível também são conhecidos como *variáveis locais*. Você declará-las com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), com ou sem o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave.  
  
 Escopo de procedimento e bloco estão intimamente relacionados. Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode pensar a variável como tendo o escopo de bloco, onde o bloco é todo o procedimento.  
  
> [!NOTE]
>  Todos os elementos locais, mesmo se forem `Static` as variáveis são particulares ao procedimento em que aparecem. Você não pode declarar qualquer elemento usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave dentro de um procedimento.  
  
### <a name="module-scope"></a>Escopo de módulo  
 Para sua conveniência, o termo simples *nível de módulo* se aplica igualmente a módulos, classes e estruturas. Você pode declarar elementos nesse nível, colocando a instrução de declaração fora de qualquer procedimento ou bloco, mas dentro do módulo, classe ou estrutura.  
  
 Quando você fizer uma declaração no nível de módulo, o nível de acesso que você escolha determina o escopo. O namespace que contém o módulo, classe ou estrutura também afeta o escopo.  
  
 Os elementos para os quais você deve declarar [privada](../../../../visual-basic/language-reference/modifiers/private.md) nível de acesso estão disponíveis para cada procedimento desse módulo, mas não para qualquer código em um módulo diferente. O `Dim` instrução no nível de módulo padrão é `Private` se você não usar quaisquer palavras-chave de nível de acesso. No entanto, você pode fazer o nível de escopo e o acesso mais óbvio, usando o `Private` palavra-chave no `Dim` instrução.  
  
 No exemplo a seguir, todos os procedimentos definidos no módulo podem se referir à variável de cadeia de caracteres `strMsg`. Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Escopo de Namespace  
 Se você declarar um elemento no nível de módulo usando o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) ou [público](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave, ele fica disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado. Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Escopo de Namespace inclui namespaces aninhados. Um elemento disponível dentro de um namespace também está disponível de dentro de qualquer namespace aninhado dentro desse namespace.  
  
 Se seu projeto não contém nenhum [declaração de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), tudo no projeto está no mesmo namespace. Nesse caso, o escopo de namespace pode ser pensado como escopo do projeto. `Public` elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que referencia o seu projeto.  
  
## <a name="choice-of-scope"></a>Opção de escopo  
 Quando você declara uma variável, você deve manter em mente os seguintes pontos ao escolher seu escopo.  
  
### <a name="advantages-of-local-variables"></a>Vantagens de variáveis locais  
 Variáveis locais são uma boa escolha para qualquer tipo de cálculo temporário, pelos seguintes motivos:  
  
-   **Prevenção de conflitos de nome.** Nomes de variável local não são suscetíveis a entrar em conflito. Por exemplo, você pode criar vários procedimentos diferentes que contém uma variável chamada `intTemp`. Desde que cada `intTemp` é declarado como uma variável local, cada procedimento reconhece apenas sua própria versão do `intTemp`. Qualquer procedimento pode alterar o valor em seu local `intTemp` sem afetar `intTemp` variáveis em outros procedimentos.  
  
-   **Consumo de memória.** As variáveis locais consomem memória somente enquanto seu procedimento está sendo executado. Sua memória é liberada quando o procedimento retorna ao código de chamada. Por outro lado, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) e [estático](../../../../visual-basic/language-reference/modifiers/static.md) variáveis consomem recursos de memória até que seu aplicativo é interrompido, portanto, use-as quando necessário. *Variáveis de instância* consomem memória enquanto sua instância continuará a existir, o que as torna menos eficiente do que as variáveis locais, mas potencialmente mais eficiente do que `Shared` ou `Static` variáveis.  
  
### <a name="minimizing-scope"></a>Minimizando o escopo  
 Em geral, ao declarar qualquer variável ou constante, é boa prática para tornar o escopo tão restrito quanto possível (o escopo de bloco é o menor). Isso ajuda a conservar a memória e minimiza as chances de seu código erroneamente referir-se a variável errada. Da mesma forma, você deve declarar uma variável para ser [estático](../../../../visual-basic/language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.  
  
## <a name="see-also"></a>Consulte também

- [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Como: Controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
