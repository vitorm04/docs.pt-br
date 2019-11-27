---
title: Declaração de variável do objeto
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
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351810"
---
# <a name="object-variable-declaration-visual-basic"></a>Declaração de variável do objeto (Visual Basic)
Você usa uma instrução de declaração normal para declarar uma variável de objeto. Para o tipo de dados, você especifica um `Object` (ou seja, o [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou uma classe mais específica da qual o objeto deve ser criado.  
  
 Declarar uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=nameWithType>.  
  
 Quando você declara uma variável com uma classe de objeto específica, ela pode acessar todos os métodos e propriedades expostos por essa classe e as classes das quais ela é herdada. Se você declarar a variável com <xref:System.Object>, ela poderá acessar somente os membros da classe <xref:System.Object>, a menos que você desative `Option Strict Off` para permitir a ligação tardia.  
  
## <a name="declaration-syntax"></a>Sintaxe de Declaração  
 Use a sintaxe a seguir para declarar uma variável de objeto:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Você também pode especificar [público](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privado](../../../../visual-basic/language-reference/modifiers/private.md), [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md)ou [estático](../../../../visual-basic/language-reference/modifiers/static.md) na declaração. As seguintes declarações de exemplo são válidas:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Associação tardia e Associação antecipada  
 Às vezes, a classe específica é desconhecida até que seu código seja executado. Nesse caso, você deve declarar a variável de objeto com o tipo de dados `Object`. Isso cria uma referência geral para qualquer tipo de objeto e a classe específica é atribuída em tempo de execução. Isso é chamado de *associação tardia*. A associação tardia requer tempo de execução adicional. Ele também limita seu código aos métodos e às propriedades da classe que você atribuiu mais recentemente a ele. Isso pode causar erros de tempo de execução se o seu código tentar acessar membros de uma classe diferente.  
  
 Quando você conhece a classe específica em tempo de compilação, deve declarar a variável de objeto para ser dessa classe. Isso é chamado de *associação inicial*. A ligação antecipada melhora o desempenho e garante o acesso do código a todos os métodos e propriedades da classe específica. Nas declarações de exemplo anteriores, se a variável `objA` usar somente objetos da classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, você deverá especificar `As System.Windows.Forms.Label` em sua declaração.  
  
### <a name="advantages-of-early-binding"></a>Vantagens da associação inicial  
 Declarar uma variável de objeto como uma classe específica oferece várias vantagens:  
  
- Verificação automática de tipo  
  
- Acesso garantido a todos os membros da classe específica  
  
- Suporte do Microsoft IntelliSense no editor de códigos  
  
- Melhor legibilidade do seu código  
  
- Menos erros em seu código  
  
- Erros capturados em tempo de compilação em vez de tempo de execução  
  
- Execução de código mais rápida  
  
## <a name="access-to-object-variable-members"></a>Acesso a membros de variável de objeto  
 Quando `Option Strict` é ativado `On`, uma variável de objeto pode acessar somente os métodos e as propriedades da classe com a qual você o declara. O exemplo a seguir mostra isso.  
  
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
  
 Neste exemplo, `p` pode usar somente os membros da própria classe <xref:System.Object>, que não incluem a propriedade `Left`. Por outro lado, `q` foi declarado como sendo do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da classe <xref:System.Windows.Forms.Label> no namespace <xref:System.Windows.Forms>.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilidade de variáveis de objeto  
 Ao trabalhar com objetos em uma hierarquia de herança, você tem a opção de qual classe usar para declarar suas variáveis de objeto. Ao fazer essa escolha, você deve balancear a flexibilidade da atribuição de objeto contra o acesso a membros de uma classe. Por exemplo, considere a hierarquia de herança que leva à classe de <xref:System.Windows.Forms.Form?displayProperty=nameWithType>:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Suponha que seu aplicativo defina uma classe de formulário chamada `specialForm`, que herda da classe <xref:System.Windows.Forms.Form>. Você pode declarar uma variável de objeto que se refere especificamente a `specialForm`, como mostra o exemplo a seguir.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 A declaração no exemplo anterior limita a variável `nextForm` a objetos da classe `specialForm`, mas também torna todos os métodos e propriedades de `specialForm` disponíveis para `nextForm`, bem como todos os membros de todas as classes das quais `specialForm` herda.  
  
 Você pode tornar uma variável de objeto mais geral declarando-a como sendo do tipo <xref:System.Windows.Forms.Form>, como mostra o exemplo a seguir.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 A declaração no exemplo anterior permite que você atribua qualquer formulário em seu aplicativo para `anyForm`. No entanto, embora `anyForm` possa acessar todos os membros da classe <xref:System.Windows.Forms.Form>, ela não pode usar nenhum dos métodos ou propriedades adicionais definidos para formulários específicos, como `specialForm`.  
  
 Todos os membros de uma classe base estão disponíveis para classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Como acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
