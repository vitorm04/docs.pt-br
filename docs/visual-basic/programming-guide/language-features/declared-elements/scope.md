---
title: "Escopo no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "escopo de bloco"
  - "elementos declarados, escopo"
  - "níveis de escopo"
  - "nível de módulo"
  - "escopo de módulo"
  - "namespaces, escopo"
  - "escopo de procedimento"
  - "procedimentos, escopo"
  - "escopo, sobre escopo"
  - "escopo, elementos declarados"
  - "escopo, níveis"
  - "escopo, Visual Basic"
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Escopo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O *escopo* de um elemento declarado é o conjunto de todo o código que pode referir\-se a ele sem qualificar seu nome ou tornando\-o disponível por um [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  Um elemento pode ter escopo em um dos seguintes níveis:  
  
|Level|Descrição|  
|-----------|---------------|  
|Escopo de bloco|Disponível apenas dentro do bloco de código no qual é declarada|  
|Escopo de Procedimento|Disponível para todo o código dentro do procedimento no qual é declarado|  
|Escopo de Módulo|Disponível para todo o código dentro do módulo, classe ou estrutura no qual é declarado|  
|Escopo de Namespace \(Espaço de Nomes\)|Disponível para todo o código dentro do namespace no qual é declarado|  
  
 Esses níveis de escopo aumentam a partir de menor \(bloco\) para o mais largo \(namespace\), onde *escopo mais restrito* significa que um menor conjunto de código pode se referir ao elemento sem qualificação.  Para obter mais informações, consulte " Níveis de Escopo " nessa página.  
  
## Especificação de Escopo e Definição de Variáveis  
 Você especifica o escopo de um elemento ao declará\-lo.  O escopo pode depender os seguintes fatores:  
  
-   A região \(bloco, procedimento, módulo, de classe ou estrutura\) na qual você declara o elemento  
  
-   O namespace que contém a declaração do elemento  
  
-   O nível de acesso que você declara para o elemento  
  
 Tome cuidado ao definir variáveis com o mesmo nome mas escopos diferentes, pois fazer isso pode levar a resultados inesperados.  Para obter mais informações, consulte [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Níveis de Escopo  
 Um elemento de programação está disponível em toda a região em que você o declara.  Todo o código na mesma região pode referir\-se ao elemento sem qualificar seu nome.  
  
### Escopo de Bloco  
 Um bloco é um conjunto de instruções envolto em instruções de declaração de ínicio e término , como o seguinte:  
  
-   `Do` e `Loop`  
  
-   `For`\[`Each`\] e `Next`.  
  
-   `If` e `End If`  
  
-   `Select` e `End Select`  
  
-   `SyncLock` e `End SyncLock`  
  
-   `Try` e `End Try`  
  
-   `While` e `End While`  
  
-   `With` e `End With`  
  
 Se você declarar uma variável em um bloco, você poderá usá\-la apenas dentro desse bloco.  No exemplo a seguir, o escopo da variável inteira `cube` é o bloco entre `If` e `End If`,e você pode não mais se referir a `cube` quando a execução passa para fora do bloco.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Mesmo se o escopo de uma variável for limitado a um bloco, sua vida útil ainda dura todo o procedimento.  Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco reterá seu valor anterior.  Para evitar resultados inesperados em casos como esse, é prudente inicializar variáveis de bloco no início do bloco.  
  
### Escopo de Procedimento  
 Um elemento declarado dentro de um procedimento não está disponível fora desse procedimento.  Somente o procedimento que contém a declaração pode usá\-lo.  Variáveis nesse nível são conhecidas como  *variáveis locais*.  Você declará\-las com [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), com ou sem a palavra\-chave [Estático](../../../../visual-basic/language-reference/modifiers/static.md).  
  
 Escopos de procedimento e bloco estão intimamente relacionadas.  Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode pensar a variável como se tivesse escopo de bloco, onde o bloco é todo o procedimento.  
  
> [!NOTE]
>  Todos os elementos locais, mesmo se forem variáveis `Static`, são particulares ao procedimento em que aparecem.  Você não é possível declarar qualquer elemento usando a  palavra\-chave [Público](../../../../visual-basic/language-reference/modifiers/public.md) dentro de um procedimento.  
  
### Escopo de Módulo  
 Para sua conveniência, o termo simples*nível de módulo*  aplica\-se igualmente a módulos, classes e estruturas.  Você pode declarar elementos nesse nível, colocando a instrução de declaração fora de qualquer procedimento ou bloco mas dentro do módulo, classe ou estrutura.  
  
 Quando você faz uma declaração no nível do módulo, o nível de acesso escolhido determina o escopo.  O namespace que contém o módulo, classe ou estrutura também influencia o escopo.  
  
 Os elementos para os quais você declarar o nível de acesso[Particular](../../../../visual-basic/language-reference/modifiers/private.md) estão disponíveis para cada procedimento desse módulo, mas não para qualquer código em um módulo diferente.  A instrução `Dim` em nível de módulo tem por padrão `Private` se você não usar nenhuma palavras\-chave de acesso de nível.  No entanto, você pode fazer o nível de escopo e o acesso mais óbvio usando a  palavra\-chave `Private` na instrução `Dim`.  
  
 No exemplo anterior, todos os procedimentos definidos no módulo podem referir\-se à variável  `strMsg` .  Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável `strMsg` em uma caixa de diálogo.  
  
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
  
### Escopo de Namespace \(Espaço de Nomes\)  
 Se você declarar um elemento no nível de módulo usando uma a palavra\-chave [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Público](../../../../visual-basic/language-reference/modifiers/public.md), ele fica disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado.  Com a seguinte alteração ao exemplo anterior, a variável de sequência de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 O escopo de namespace inclui namespaces aninhados.  Um elemento disponível dentro de um namespace também está disponível em qualquer namespace aninhado dentro do primeiro.  
  
 Se o projeto não contém nenhum [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), tudo no projeto está no mesmo namespace.  Nesse caso, o escopo de espaço para nome pode ser pensado como escopo do projeto.  `Public`elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que faz referência a seu projeto.  
  
## Opção de Escopo  
 Ao declarar uma variável, tenha em mente os seguintes pontos ao escolher seu escopo.  
  
### Vantagens de Variáveis Locais  
 As variáveis locais são uma boa opção para qualquer tipo de cálculo temporário, pelos seguintes motivos:  
  
-   **Prevenção de Conflitos de Nome.** Nomes de variáveis locais são não suscetíveis a entrar em conflito.  Por exemplo, você pode criar vários procedimentos diferentes que contém uma variável chamada `intTemp`.  Contanto que cada `intTemp` é declarada como um variável local, cada procedimento reconhece apenas sua própria versão do `intTemp`.  Qualquer procedimento pode alterar o valor em seu `intTemp` local sem afetar as variáveis `intTemp` nos outros procedimentos.  
  
-   **Consumo de Memória.** As variáveis locais consomem memória somente enquanto o procedimento estiver sendo executado.  Sua memória é liberada quando o procedimento retorna para o código de chamada.  Por contraste,  variáveis [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) e [Estático](../../../../visual-basic/language-reference/modifiers/static.md) consomem recursos de memória até que seu aplicativo é interrompido, portanto, use\-as somente quando necessário.  *Variáveis de Instância*  consomem memória enquanto sua instância continu a existir, o que as torna menos eficiente do que as variáveis locais, mas possivelmente mais eficiente do que variáveis `Shared` ou `Static`.  
  
### Minimizando o Escopo  
 Em geral, quando declarar qualquer variável ou constante, é boa prática de programação tornar o escopo tão restrito quanto possível possíveis \(escopo de bloco é o menor\).  Isso ajuda a conservar a memória e minimiza as chances de seu código erroneamente referir\-se a variável errada.  Da mesma forma, você deve declarar uma variável como [Estático](../../../../visual-basic/language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.  
  
## Consulte também  
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Como controlar o escopo de uma variável](../Topic/How%20to:%20Control%20the%20Scope%20of%20a%20Variable%20\(Visual%20Basic\).md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)