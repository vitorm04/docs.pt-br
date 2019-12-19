---
title: Compartilhado
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349126"
---
# <a name="shared-visual-basic"></a>Compartilhado (Visual Basic)
Especifica que um ou mais elementos de programação declarados estão associados a uma classe ou estrutura em tamanho grande, e não com uma instância específica da classe ou estrutura.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="when-to-use-shared"></a>Quando usar compartilhado  
 O compartilhamento de um membro de uma classe ou estrutura torna-o disponível para cada instância, em vez de não *compartilhado*, em que cada instância mantém sua própria cópia. Isso é útil, por exemplo, se o valor de uma variável se aplicar a todo o aplicativo. Se você declarar que a variável seja `Shared`, todas as instâncias acessarão o mesmo local de armazenamento e, se uma instância alterar o valor da variável, todas as instâncias acessarão o valor atualizado.  
  
 O compartilhamento não altera o nível de acesso de um membro. Por exemplo, um membro de classe pode ser compartilhado e privado (acessível somente de dentro da classe), ou não compartilhado e público. Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Regras  
  
- **Contexto de declaração.** Você pode usar `Shared` somente no nível do módulo. Isso significa que o contexto de declaração para um elemento de `Shared` deve ser uma classe ou estrutura e não pode ser um arquivo de origem, namespace ou procedimento.  
  
- **Modificadores combinados.** Não é possível especificar `Shared` juntamente [com substituições](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)ou [Static](../../../visual-basic/language-reference/modifiers/static.md) na mesma declaração.  
  
- **Acess.** Você acessa um elemento compartilhado qualificando-o com seu nome de classe ou estrutura, não com o nome da variável de uma instância específica de sua classe ou estrutura. Você não precisa nem criar uma instância de uma classe ou estrutura para acessar seus membros compartilhados.  
  
     O exemplo a seguir chama o procedimento compartilhado <xref:System.Double.IsNaN%2A> exposto pela estrutura <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Compartilhamento implícito.** Você não pode usar o modificador `Shared` em uma [instrução const](../../../visual-basic/language-reference/statements/const-statement.md), mas as constantes são compartilhadas implicitamente. Da mesma forma, você não pode declarar um membro de um módulo ou uma interface para ser `Shared`, mas eles são compartilhados implicitamente.  
  
## <a name="behavior"></a>Comportamento  
  
- **Repositório.** Uma variável ou evento compartilhado é armazenado na memória apenas uma vez, independentemente de quantas instâncias você criar de sua classe ou estrutura. Da mesma forma, um procedimento compartilhado ou propriedade mantém apenas um conjunto de variáveis locais.  
  
- **Acessando por meio de uma variável de instância.** É possível acessar um elemento compartilhado qualificando-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura. Embora isso normalmente funcione conforme o esperado, o compilador gera uma mensagem de aviso e faz o acesso por meio do nome da classe ou da estrutura em vez da variável.  
  
- **Acessando por meio de uma expressão de instância.** Se você acessar um elemento compartilhado por meio de uma expressão que retorna uma instância de sua classe ou estrutura, o compilador fará o acesso por meio do nome da classe ou da estrutura em vez de avaliar a expressão. Isso produzirá resultados inesperados se você pretende que a expressão execute outras ações, bem como o retorno da instância. O exemplo a seguir ilustra essa situação.  
  
    ```vb
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
  
     No exemplo anterior, o compilador gera uma mensagem de aviso, ambas as vezes, o código acessa a variável compartilhada `total` por meio de uma instância. Em cada caso, ele faz o acesso diretamente por meio da classe `shareTotal` e não faz uso de nenhuma instância. No caso da chamada pretendida para o procedimento `returnClass`, isso significa que ele não gera uma chamada para `returnClass`, portanto, a ação adicional de exibir "função returnClass () chamada" não é executada.  
  
 O modificador de `Shared` pode ser usado nesses contextos:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Estático](../../../visual-basic/language-reference/modifiers/static.md)
- [Tempo de vida em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
