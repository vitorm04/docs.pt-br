---
title: Compartilhado (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shared
dev_langs:
- VB
helpviewer_keywords:
- Shared keyword
- members, shared
- shared members
- nonshared
- shared elements
- elements, shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b4f87c7d672d38367f3f12a0a9f44c4247eaa0b9
ms.lasthandoff: 03/13/2017

---
# <a name="shared-visual-basic"></a>Compartilhado (Visual Basic)
Especifica que um ou mais elementos de programação declarados estão associados com uma classe ou estrutura em geral e não com uma instância específica da classe ou estrutura.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="when-to-use-shared"></a>Para usar compartilhamento  
 Compartilhar um membro de uma classe ou estrutura torna disponível para cada instância, em vez de *compartilhados*, onde cada instância tem sua própria cópia. Isso é útil, por exemplo, se o valor de uma variável se aplica a todo o aplicativo. Se você declarar essa variável como `Shared`, em seguida, todas as instâncias acessam o mesmo local de armazenamento e se uma instância muda o valor da variável, todas instâncias acessam o valor atualizado.  
  
 Compartilhar não altera o nível de acesso de um membro. Por exemplo, um membro da classe pode ser compartilhado e privado (acessível somente de dentro da classe), ou não compartilhado e público. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Shared` somente no nível de módulo. Isso significa que o contexto da declaração para um `Shared` elemento deve ser uma classe ou estrutura e não pode ser um arquivo fonte, namespace ou procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `Shared` junto com [substituições](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), ou [estático](../../../visual-basic/language-reference/modifiers/static.md) na mesma declaração.  
  
-   **Acessando.** Você pode acessar um elemento compartilhado qualificando-o com seu nome de classe ou estrutura, não com o nome da variável de uma instância específica de sua classe ou estrutura. Até mesmo, você não precisa criar uma instância de uma classe ou estrutura para acessar seus membros compartilhados.  
  
     O exemplo a seguir chama o procedimento compartilhado <xref:System.Double.IsNaN%2A>exposto pelo <xref:System.Double>estrutura.</xref:System.Double> </xref:System.Double.IsNaN%2A>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Compartilhamento implícito.** Não é possível usar o `Shared` modificador em um [instrução Const](../../../visual-basic/language-reference/statements/const-statement.md), mas constantes são implicitamente compartilhadas. Da mesma forma, você não pode declarar um membro de um módulo ou interface como `Shared`, mas eles são implicitamente compartilhados.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Armazenamento.** Uma variável compartilhada ou evento é armazenado na memória somente uma vez, não importa quantas vezes você criar de sua classe ou estrutura. Da mesma forma, um procedimento compartilhado ou propriedade contém somente um conjunto de variáveis locais.  
  
-   **Acessando através de uma variável de instância.** É possível acessar um elemento compartilhado qualificando-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura. Embora isso geralmente funciona conforme o esperado, o compilador gera uma mensagem de aviso e faz o acesso através do nome da classe ou estrutura em vez da variável.  
  
-   **Acessando através de uma expressão de instância.** Se você acessar um elemento compartilhado através de uma expressão que retorna uma instância de sua classe ou estrutura, o compilador faz o acesso através do nome da classe ou estrutura em vez de avaliar a expressão. Isso produz resultados inesperados se você pretendia que a expressão para executar outras ações, bem como retornar a instância. O exemplo a seguir ilustra essa situação.  
  
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
  
     No exemplo anterior, o compilador gera uma mensagem de aviso nas duas vezes que o código acessa a variável compartilhada `total` através de uma instância. Em cada caso ele faz o acesso diretamente através da classe `shareTotal` e não faz uso de nenhuma instância. No caso da chamada pretendida ao procedimento `returnClass`, isso significa que ele nem gera uma chamada para `returnClass`, portanto, a ação adicional de mostrar "Function returnClass () chamado" não é executada.  
  
 O `Shared` modificador pode ser usado nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Estático](../../../visual-basic/language-reference/modifiers/static.md)   
 [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
