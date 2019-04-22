---
title: Declaração de variável do objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837644"
---
# <a name="object-variable-declaration-visual-basic"></a>Declaração de variável do objeto (Visual Basic)
Você pode usar uma instrução de declaração normal para declarar uma variável de objeto. Para o tipo de dados, você especificar `Object` (ou seja, o [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou uma classe mais específica do qual o objeto deve ser criado.  
  
 Declarar uma variável como `Object` é o mesmo que declarar como <xref:System.Object?displayProperty=nameWithType>.  
  
 Quando você declara uma variável com uma classe de objeto específico, ele pode acessar todos os métodos e propriedades expostas pela classe e as classes da qual ela herda. Se você declarar a variável com <xref:System.Object>, ele pode acessar somente os membros do <xref:System.Object> classe, a menos que você ative `Option Strict Off` para permitir a associação tardia.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 Use a seguinte sintaxe para declarar uma variável de objeto:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Você também pode especificar [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privada](../../../../visual-basic/language-reference/modifiers/private.md), [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ou [estático](../../../../visual-basic/language-reference/modifiers/static.md) na declaração. As declarações de exemplo a seguir são válidas:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Associação tardia e a vinculação inicial  
 Às vezes, a classe específica é desconhecida até que seu código seja executado. Nesse caso, você deve declarar a variável de objeto com o `Object` tipo de dados. Isso cria uma referência geral para qualquer tipo de objeto, e a classe específica é atribuída em tempo de execução. Isso é chamado *ligação tardia*. Associação tardia exige mais tempo de execução. Ela também limita seu código para os métodos e propriedades da classe que mais recentemente atribuídos a ele. Isso pode causar erros de tempo de execução se seu código tentar acessar membros de outra classe.  
  
 Quando você souber a classe específica no tempo de compilação, você deve declarar a variável de objeto para ser daquela classe. Isso é chamado de *associação inicial*. Associação antecipada melhora o desempenho e garante a seu código de acesso para todos os métodos e propriedades da classe específica. Nas declarações de exemplo anterior, se a variável `objA` usa apenas os objetos da classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, você deve especificar `As System.Windows.Forms.Label` na sua declaração.  
  
### <a name="advantages-of-early-binding"></a>Vantagens da associação inicial  
 Declarar uma variável de objeto como uma classe específica oferece várias vantagens:  
  
-   Verificação de tipo automática  
  
-   A garantia de acesso a todos os membros da classe específica  
  
-   Suporte do Microsoft IntelliSense no Editor de códigos  
  
-   Melhor legibilidade do código  
  
-   Menos erros em seu código  
  
-   Os erros detectados em tempo de compilação, em vez de tempo de execução  
  
-   Execução de código mais rápida  
  
## <a name="access-to-object-variable-members"></a>Acesso a membros de variável de objeto  
 Quando `Option Strict` estiver desativado `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual você declará-la. O exemplo a seguir ilustra essa situação.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object> classe em si, que não incluem o `Left` propriedade. Por outro lado, `q` tiver sido declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label> classe o <xref:System.Windows.Forms> namespace.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilidade de variáveis de objeto  
 Ao trabalhar com objetos em uma hierarquia de herança, você tem a opção de qual classe usar para declarar as variáveis de objeto. Ao fazer essa opção, você deve equilibrar a flexibilidade de atribuição de objeto contra o acesso a membros de uma classe. Por exemplo, considere a hierarquia de herança que leva para o <xref:System.Windows.Forms.Form?displayProperty=nameWithType> classe:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Suponha que seu aplicativo define uma classe de formulário chamada `specialForm`, que herda da classe <xref:System.Windows.Forms.Form>. Você pode declarar uma variável de objeto refere-se especificamente ao `specialForm`, como mostra o exemplo a seguir.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 A declaração no exemplo anterior limita a variável `nextForm` para objetos da classe `specialForm`, mas também torna todos os métodos e propriedades de `specialForm` disponíveis para `nextForm`, assim como todos os membros de todas as classes da qual `specialForm` herda.  
  
 Você pode fazer uma variável de objeto mais geral ao declará-la para ser do tipo <xref:System.Windows.Forms.Form>, como mostra o exemplo a seguir.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 A declaração no exemplo anterior permite que você atribua qualquer formulário em seu aplicativo para `anyForm`. No entanto, embora `anyForm` pode acessar todos os membros da classe <xref:System.Windows.Forms.Form>, não é possível usar qualquer um dos outros métodos ou propriedades definidas para formulários específicos, como `specialForm`.  
  
 Todos os membros de uma classe base estão disponíveis para as classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: Declare uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Como: Acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
