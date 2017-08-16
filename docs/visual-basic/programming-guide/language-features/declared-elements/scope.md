---
title: Escopo no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- module scope
- scope, levels
- module level
- procedures, scope
- declared elements, scope
- namespaces, scope
- scope, declared elements
- scope, about scope
- levels of scope
- block scope
- scope, Visual Basic
- procedure scope
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 28e096f9e35a4981d66752f204ed57b25116e8c8
ms.lasthandoff: 03/13/2017

---
# <a name="scope-in-visual-basic"></a>Escopo no Visual Basic
O *escopo* de um elemento declarado é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome ou tornando-o disponível por meio de um [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Um elemento pode ter escopo em um dos seguintes níveis:  
  
|Nível|Descrição|  
|-----------|-----------------|  
|Escopo de bloco|Disponível apenas dentro do código de bloco no qual é declarado|  
|Escopo de procedimento|Disponível para todo o código dentro do procedimento no qual é declarado|  
|Escopo de módulo|Disponível para todo o código dentro do módulo, classe ou estrutura na qual ela é declarada|  
|Escopo de Namespace|Disponível para todo o código no namespace no qual ela é declarada|  
  
 Esses níveis de escopo aumentam a partir de menor (bloco) para o mais largo (namespace), onde *escopo mais restrito* significa o menor conjunto de código pode se referir ao elemento sem qualificação. Para obter mais informações, consulte "Níveis de escopo" nessa página.  
  
## <a name="specifying-scope-and-defining-variables"></a>Especificação de escopo e definição de variáveis  
 Especifique o escopo de um elemento ao declará-lo. O escopo pode depender dos seguintes fatores:  
  
-   A região (bloco, procedimento, módulo, classe ou estrutura) na qual você declara o elemento  
  
-   O namespace que contém a declaração do elemento  
  
-   O nível de acesso que você declara para o elemento  
  
 Tenha cuidado ao definir variáveis com o mesmo nome mas escopo diferente, porque isso pode levar a resultados inesperados. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Níveis de escopo  
 Um elemento de programação está disponível em toda a região em que você declare. Todo o código na mesma região pode se referir ao elemento sem qualificar seu nome.  
  
### <a name="block-scope"></a>Escopo de bloco  
 Um bloco é um conjunto de instruções entre Iniciando e encerrando instruções de declaração, como o seguinte:  
  
-   `Do` e `Loop`  
  
-   `For`[`Each`] and`Next`  
  
-   `If` e `End If`  
  
-   `Select` e `End Select`  
  
-   `SyncLock` e `End SyncLock`  
  
-   `Try` e `End Try`  
  
-   `While` e `End While`  
  
-   `With` e `End With`  
  
 Se você declarar uma variável dentro de um bloco, você pode usá-lo apenas dentro desse bloco. No exemplo a seguir, o escopo da variável de inteiro `cube` é o bloco entre `If` e `End If`, e você não pode se referir a `cube` quando a execução passa para fora do bloco.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Mesmo se o escopo de uma variável é limitado a um bloco, sua vida útil ainda é que todo o procedimento. Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco reterá seu valor anterior. Para evitar resultados inesperados, nesse caso, é prudente inicializar variáveis de bloco no início do bloco.  
  
### <a name="procedure-scope"></a>Escopo de procedimento  
 Um elemento declarado dentro de um procedimento não está disponível fora desse procedimento. Somente o procedimento que contém a declaração pode usá-lo. Variáveis nesse nível são também conhecidos como *variáveis locais*. Você declará-las com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), com ou sem o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave.  
  
 Escopo de procedimento e bloco estão intimamente relacionados. Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode pensar a variável como tendo escopo de bloco, onde o bloco é todo o procedimento.  
  
> [!NOTE]
>  Todos os elementos locais, mesmo se forem `Static` as variáveis são particulares ao procedimento em que aparecem. Você não pode declarar qualquer elemento usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave dentro de um procedimento.  
  
### <a name="module-scope"></a>Escopo de módulo  
 Para sua conveniência, o termo simples *nível de módulo* aplica-se igualmente a módulos, classes e estruturas. Você pode declarar elementos nesse nível, colocando a instrução de declaração fora de qualquer procedimento ou bloco mas dentro do módulo, classe ou estrutura.  
  
 Quando você faz uma declaração no nível de módulo, o nível de acesso escolhido determina o escopo. O namespace que contém o módulo, classe ou estrutura também influencia o escopo.  
  
 Elementos para os quais você declarar [particular](../../../../visual-basic/language-reference/modifiers/private.md) nível de acesso estão disponíveis para cada procedimento desse módulo, mas não para qualquer código em um módulo diferente. O `Dim` instrução no nível de módulo padrão é `Private` se você não usar as palavras-chave de nível de acesso. No entanto, você pode fazer o nível de escopo e o acesso mais óbvio usando o `Private` palavra-chave no `Dim` instrução.  
  
 No exemplo a seguir, todos os procedimentos definidos no módulo podem referir-se à variável de cadeia de caracteres `strMsg`. Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.  
  
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
 Se você declarar um elemento no nível de módulo usando o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) ou [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave, ele fica disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado. Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Escopo de Namespace inclui namespaces aninhados. Um elemento disponível dentro de um namespace também está disponível em qualquer namespace aninhado dentro desse namespace.  
  
 Se o projeto não contém nenhum [declaração de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), tudo no projeto está no mesmo namespace. Nesse caso, o escopo de namespace pode ser pensado como escopo do projeto. `Public`elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que referencia o seu projeto.  
  
## <a name="choice-of-scope"></a>Opção de escopo  
 Quando você declara uma variável, você deve manter em mente os seguintes pontos ao escolher seu escopo.  
  
### <a name="advantages-of-local-variables"></a>Vantagens de variáveis locais  
 Variáveis locais são uma boa opção para qualquer tipo de cálculo temporário, pelos seguintes motivos:  
  
-   **Prevenção de conflitos de nome.** Nomes de variáveis locais não são suscetíveis a entrar em conflito. Por exemplo, você pode criar vários procedimentos diferentes que contém uma variável chamada `intTemp`. Contanto que cada `intTemp` é declarado como uma variável local, cada procedimento reconhece apenas sua própria versão do `intTemp`. Qualquer procedimento pode alterar o valor em seu local `intTemp` sem afetar `intTemp` variáveis em outros procedimentos.  
  
-   **Consumo de memória.** Variáveis locais consomem memória somente enquanto seu procedimento está sendo executado. A memória é liberada quando o procedimento retorna para o código de chamada. Por outro lado, [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) e [estático](../../../../visual-basic/language-reference/modifiers/static.md) variáveis consomem recursos de memória até que seu aplicativo é interrompido, portanto, use-as somente quando necessário. *Variáveis de instância* consomem memória enquanto sua instância continua a existir, o que as torna menos eficiente do que as variáveis locais, mas possivelmente mais eficiente do que `Shared` ou `Static` variáveis.  
  
### <a name="minimizing-scope"></a>Minimizando o escopo  
 Em geral, quando declarar qualquer variável ou constante, é boa prática para tornar o escopo mais estreita possível de programação (escopo de bloco é o menor). Isso ajuda a conservar a memória e minimiza as chances de seu código erroneamente referir-se a variável errada. Da mesma forma, você deve declarar uma variável para ser [estático](../../../../visual-basic/language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Como: controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
