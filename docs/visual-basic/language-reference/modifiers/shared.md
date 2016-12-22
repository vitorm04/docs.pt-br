---
title: "Compartilhado (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Shared"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elementos, shared"
  - "membros, shared"
  - "não compartilhados"
  - "elementos compartilhados"
  - "palavra-chave Shared"
  - "membros compartilhados"
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Compartilhado (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um ou mais elementos de programação declaradados estão associados com uma classe ou estrutura em geral, e não com uma instância específica da classe ou estrutura.  
  
## Comentários  
  
## Para usar Compartilhamento  
 Compartilhamento de um membro de uma classe ou estrutura torna disponível para cada instância, em vez de  *não compartilhados*, onde cada instância manterá sua própria cópia.  Isso é útil, por exemplo, se o valor da variável vale para toda a aplicação.  Se você declara essa variável como `Shared`, todas suas instância acessam o mesmo local de armazenamento, se uma instância muda o valor da variável, todas instâncias acessam o valor atualizado.  
  
 Compartilhar não altera o nível de acesso de um membro.  Por exemplo, um membro da classe pode ser compartilhado e privado \(acessível somente de dentro da classe\), ou não compartilhado e público.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `Shared` somente no nível de módulo.  Isso significa que o contexto da declaração para um elemento `Shared` deve ser uma classe ou estrutura, e não um arquivo fonte, namespace ou procedimento.  
  
-   **Modificadores Combinados.** Não é possível especificar `Shared` em conjunto com [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md), [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), ou [Estático](../../../visual-basic/language-reference/modifiers/static.md) na mesma declaração.  
  
-   **Acessando.** Você acessa um elemento compartilhado qualificando\-o com seu nome de estrutura ou classe, não com o nome da variável de uma instância específica de sua classe ou estrutura.  Você não precisa nem criar uma instância da classe ou estrutura para acessar seus membros compartilhados.  
  
     O exemplo a seguir chama o procecimento compartilhado <xref:System.Double.IsNaN%2A> exposto pela estrutura <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Compartilhamento Implícito.** Não é possível usar o `Shared` modificador em um [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md), mas constantes são compartilhadas implicitamente.  Similarmente, você não pode declarar um membro de um módulo ou interface como `Shared`, mas eles são implicitamente compartilhados.  
  
## Comportamento  
  
-   **Armazenamento.** Uma variável compartilhada ou evento é armazenado na memória somente uma vez, não importa quantas vezes você crie sua classe ou estrutura.  Similarmente, um procedimento compartilhado ou propriedade contém somente um conjunto de variáveis locais.  
  
-   **Acessando através de uma Variável de Instância** É possível acessar um elemento compartilhado qualificando\-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura.  Apesar disso geralmente funcionar como esperado, o compilador gera uma mensagem de aviso e faz o acesso através do nome da classe ou estrutura ao invés da variável.  
  
-   **Acessando através de uma Expressão de Instância** Se você acessa um elemento compartilhado através de uma expressão que retorna uma instância de uma classe ou estrutura, o compilador faz o acesso através do nome ou estrutura da classe em vez de analisar a expressão.  Isso pode produzir resultados inesperados se você pretendia que a expressão executasse outras ações além de retornar a instância.  O exemplo a seguir ilustra isto:  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     No exemplo anterior, o compilador gera uma mensagem de aviso nas duas vezes que o código acessa a variável compartilhada `total` através de uma instância.  Em cada caso ele faz o acesso diretamente através da classe `shareTotal` e não faz uso de nenhuma instância.  No caso da chamada pretendida ao procedimento `returnClass`, isso significa que ele nem gera um chamado a `returnClass`, de forma que a ação adicional de mostrar "Function returnClass\(\) called" não é feita.  
  
 O modificador `Shared` pode ser utilizado nestes contextos:  
  
 [Esmaecer declaração](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução função](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Declaração Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Estático](../../../visual-basic/language-reference/modifiers/static.md)   
 [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)