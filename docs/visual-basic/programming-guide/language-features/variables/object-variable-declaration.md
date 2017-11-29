---
title: "Declaração de variável do objeto (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cdca188d778e9884f918d97eba492a29c64af826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-declaration-visual-basic"></a>Declaração de variável do objeto (Visual Basic)
Você pode usar uma declaração comum para declarar uma variável de objeto. O tipo de dados, especifique o `Object` (ou seja, o [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou uma classe mais específica da qual o objeto será criado.  
  
 Declarando uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=nameWithType>.  
  
 Quando você declara uma variável com uma classe de objeto específico, ele pode acessar todos os métodos e propriedades expostas pela classe e as classes da qual ela herda. Se você declarar a variável com <xref:System.Object>, ele pode acessar somente os membros do <xref:System.Object> de classe, a menos que você ative `Option Strict Off` para permitir a associação tardia.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 Use a seguinte sintaxe para declarar uma variável de objeto:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Você também pode especificar [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privada](../../../../visual-basic/language-reference/modifiers/private.md), [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ou [estático](../../../../visual-basic/language-reference/modifiers/static.md) na declaração. As declarações de exemplo a seguir são válidas:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Associação tardia ou associação inicial  
 Às vezes, a classe específica é desconhecida até que seu código seja executado. Nesse caso, você deve declarar a variável de objeto com o `Object` tipo de dados. Isso cria uma referência geral para qualquer tipo de objeto, e a classe específica é atribuída em tempo de execução. Isso é chamado de *associação tardia*. Associação tardia requer mais tempo de execução. Ele também limita seu código para os métodos e propriedades da classe que você atribuiu a ele mais recentemente. Isso pode causar erros de tempo de execução se seu código tentar acessar membros de uma classe diferente.  
  
 Quando você souber a classe específica em tempo de compilação, você deve declarar a variável de objeto de classe. Isso é chamado de *associação inicial*. Associação antecipada melhora o desempenho e garante o acesso de código para todos os métodos e propriedades da classe específica. Nas declarações de exemplo anterior, se a variável `objA` usa apenas os objetos da classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, você deve especificar `As System.Windows.Forms.Label` na sua declaração.  
  
### <a name="advantages-of-early-binding"></a>Vantagens da associação inicial  
 Declarar uma variável de objeto como uma classe específica oferece várias vantagens:  
  
-   Verificação de tipo automática  
  
-   A garantia de acesso a todos os membros da classe específica  
  
-   Suporte da Microsoft IntelliSense no Editor de códigos  
  
-   Melhor legibilidade do código  
  
-   Menos erros no seu código  
  
-   Erros detectados no tempo de compilação em vez de tempo de execução  
  
-   Execução de código mais rápida  
  
## <a name="access-to-object-variable-members"></a>Acesso a membros de variável de objeto  
 Quando `Option Strict` está ativada `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada. O exemplo a seguir ilustra essa situação.  
  
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
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object> classe em si, que não inclui o `Left` propriedade. Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades do <xref:System.Windows.Forms.Label> classe no <xref:System.Windows.Forms> namespace.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilidade de variáveis de objeto  
 Ao trabalhar com objetos em uma hierarquia de herança, você tem uma opção de qual classe a ser usado para declarar variáveis objeto. Fazer esta opção, você deve equilibrar a flexibilidade de atribuição de objeto contra o acesso a membros de uma classe. Por exemplo, considere a hierarquia de herança que leva para o <xref:System.Windows.Forms.Form?displayProperty=nameWithType> classe:  
  
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
  
 A declaração no exemplo anterior limita a variável `nextForm` para objetos da classe `specialForm`, mas ele também torna todos os métodos e propriedades de `specialForm` disponíveis para `nextForm`, assim como todos os membros de todas as classes do qual `specialForm` herda.  
  
 Você pode fazer uma variável de objeto mais geral declarando-lo para ser do tipo <xref:System.Windows.Forms.Form>, como mostra o exemplo a seguir.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 A declaração no exemplo anterior permite que você atribua qualquer formulário em seu aplicativo para `anyForm`. No entanto, embora `anyForm` pode acessar todos os membros da classe <xref:System.Windows.Forms.Form>, ele não pode usar qualquer um dos métodos adicionais ou propriedades definidas para formulários específicos, como `specialForm`.  
  
 Todos os membros de uma classe base estão disponíveis para as classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Como acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
