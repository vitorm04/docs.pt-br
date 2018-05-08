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
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="scope-in-visual-basic"></a>Escopo no Visual Basic
O *escopo* de um elemento declarado é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome ou tornando-o disponível por meio de um [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Um elemento pode ter escopo em um dos seguintes níveis:  
  
|Nível|Descrição|  
|-----------|-----------------|  
|Escopo de bloco|Disponível somente no código do bloco no qual ela é declarada|  
|Escopo do procedimento|Disponível para todo o código dentro do procedimento no qual ela é declarada|  
|Escopo do módulo|Disponível para todo o código dentro do módulo, classe ou estrutura na qual ela é declarada|  
|Escopo de Namespace|Disponível para todo o código no namespace no qual ela é declarada|  
  
 Estes níveis de progresso de escopo de menor (bloco) para maior (namespace), onde *escopo mais restrito* significa o menor conjunto de código que pode fazer referência ao elemento sem qualificação. Para obter mais informações, consulte "Níveis de escopo" nessa página.  
  
## <a name="specifying-scope-and-defining-variables"></a>Especificação de escopo e definição de variáveis  
 Especifique o escopo de um elemento ao declare-o. O escopo pode depender dos seguintes fatores:  
  
-   A região (bloco, procedimento, módulo, classe ou estrutura) em que você declarar o elemento  
  
-   O namespace que contém a declaração do elemento  
  
-   O nível de acesso que você declara para o elemento  
  
 Tenha cuidado ao definir variáveis com o mesmo nome mas com escopos diferentes, pois isso pode levar a resultados inesperados. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Níveis de escopo  
 Um elemento de programação está disponível em toda a região em que você declare. Todo o código na mesma região pode se referir ao elemento sem qualificar seu nome.  
  
### <a name="block-scope"></a>Escopo de bloco  
 Um bloco é um conjunto de instruções entre iniciar e encerrar as instruções de declaração, como o seguinte:  
  
-   `Do` e `Loop`  
  
-   `For` [`Each`] e `Next`  
  
-   `If` e `End If`  
  
-   `Select` e `End Select`  
  
-   `SyncLock` e `End SyncLock`  
  
-   `Try` e `End Try`  
  
-   `While` e `End While`  
  
-   `With` e `End With`  
  
 Se você declarar uma variável em um bloco, você pode usá-lo somente dentro desse bloco. No exemplo a seguir, o escopo da variável de inteiro `cube` é o bloco entre `If` e `End If`, e você não pode se referir a `cube` quando a execução passa o bloco.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Mesmo se o escopo de uma variável é limitado a um bloco, sua vida útil ainda é que todo o procedimento. Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco reterá seu valor anterior. Para evitar resultados inesperados, nesse caso, é prudente inicializar variáveis de bloco no início do bloco.  
  
### <a name="procedure-scope"></a>Escopo do procedimento  
 Um elemento declarado dentro de um procedimento não está disponível fora desse procedimento. Somente o procedimento que contém a declaração pode usá-lo. Variáveis com esse nível também são conhecidas como *variáveis locais*. Você declará-los com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), com ou sem o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave.  
  
 Escopo de procedimento e bloco estão intimamente relacionados. Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode pensar a variável como tendo o escopo de bloco, onde o bloco é todo o procedimento.  
  
> [!NOTE]
>  Todos os elementos locais, mesmo se forem `Static` as variáveis são particulares ao procedimento em que aparecem. Você não pode declarar qualquer elemento usando a [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave em um procedimento.  
  
### <a name="module-scope"></a>Escopo do módulo  
 Para sua conveniência, o termo único *nível de módulo* se aplica igualmente a módulos, classes e estruturas. Você pode declarar elementos nesse nível, colocando a instrução de declaração fora de qualquer procedimento ou bloco mas dentro do módulo, classe ou estrutura.  
  
 Quando você faz uma declaração no nível de módulo, o nível de acesso que você escolha determina o escopo. O namespace que contém o módulo, classe ou estrutura também afeta o escopo.  
  
 Os elementos para os quais você declarar [privada](../../../../visual-basic/language-reference/modifiers/private.md) nível de acesso estão disponíveis para cada procedimento desse módulo, mas não para qualquer código em um módulo diferente. O `Dim` instrução no nível de módulo padrão é `Private` se você não usar as palavras-chave de nível de acesso. No entanto, você pode fazer o nível de escopo e o acesso mais óbvio usando o `Private` palavra-chave no `Dim` instrução.  
  
 No exemplo a seguir, todos os procedimentos definidos no módulo podem fazer referência à variável de cadeia de caracteres `strMsg`. Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.  
  
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
 Se você declarar um elemento no nível de módulo usando o [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave, ele fica disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado. Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Escopo de Namespace inclui namespaces aninhados. Um elemento disponível dentro de um namespace também está disponível de dentro de qualquer namespace aninhado dentro desse namespace.  
  
 Se o projeto não contém nenhum [declaração de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), tudo no projeto está no mesmo namespace. Nesse caso, o escopo de namespace pode ser considerado como escopo do projeto. `Public` elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que referencia o seu projeto.  
  
## <a name="choice-of-scope"></a>Opção de escopo  
 Quando você declara uma variável, você deve ter em mente os seguintes pontos ao escolher seu escopo.  
  
### <a name="advantages-of-local-variables"></a>Vantagens de variáveis locais  
 Variáveis locais são uma boa escolha para qualquer tipo de cálculo temporário, pelos seguintes motivos:  
  
-   **Prevenção de conflitos de nome.** Nomes de variáveis locais não são suscetíveis a entrar em conflito. Por exemplo, você pode criar vários procedimentos diferentes que contém uma variável chamada `intTemp`. Contanto que cada `intTemp` é declarado como uma variável local, cada procedimento reconhece apenas sua própria versão do `intTemp`. Qualquer procedimento pode alterar o valor em seu local `intTemp` sem afetar `intTemp` variáveis em outros procedimentos.  
  
-   **Consumo de memória.** Variáveis locais consomem memória somente enquanto o procedimento está sendo executado. A memória é liberada quando o procedimento retorna para o código de chamada. Por outro lado, [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) e [estático](../../../../visual-basic/language-reference/modifiers/static.md) variáveis consomem recursos de memória até que seu aplicativo é interrompido, portanto, use-as somente quando necessário. *Variáveis de instância* consomem memória enquanto a instância continuará a existir, o que torna menos eficiente do que as variáveis locais, mas possivelmente mais eficiente do que `Shared` ou `Static` variáveis.  
  
### <a name="minimizing-scope"></a>Minimizando o escopo  
 Em geral, ao declarar qualquer variável ou constante, é uma boa prática para tornar o escopo mais estreita possível de programação (escopo de bloco é o menor). Isso ajuda a conservar a memória e minimiza as chances de seu código erroneamente referir-se a variável errada. Da mesma forma, você deve declarar uma variável para ser [estático](../../../../visual-basic/language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Como controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
