---
title: "Declaração de variável (Visual Basic) do objeto | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- early binding
- declarations, class
- classes [Visual Basic], declaring
- binding, late and early
- object variables, declaring
- variables [Visual Basic], object
- declaring variables, object variables
- declaring classes
- late binding
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: 33
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
ms.openlocfilehash: 7dca56d1f5f6fff7cb758c9a1bfe80b30a2b4318
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-declaration-visual-basic"></a>Declaração de variável do objeto (Visual Basic)
Você usa uma declaração comum para declarar uma variável de objeto. Para o tipo de dados, você especificar `Object` (ou seja, o [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou uma classe mais específica da qual o objeto deve ser criado.  
  
 Declarar uma variável como `Object` é o mesmo que declará-la como <xref:System.Object?displayProperty=fullName>.</xref:System.Object?displayProperty=fullName>  
  
 Quando você declara uma variável com uma classe de objeto específica, ele pode acessar todos os métodos e propriedades expostas pela classe e as classes do qual ele herda. Se você declarar a variável com <xref:System.Object>, ele pode acessar somente os membros do <xref:System.Object>de classe, a menos que você ative `Option Strict Off` para permitir a ligação tardia.</xref:System.Object> </xref:System.Object>  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 Use a seguinte sintaxe para declarar uma variável de objeto:  
  
```  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Você também pode especificar [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [particular](../../../../visual-basic/language-reference/modifiers/private.md), [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ou [estático](../../../../visual-basic/language-reference/modifiers/static.md) na declaração. As seguintes declarações de exemplo são válidas:  
  
```  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Associação tardia ou associação inicial  
 Às vezes, a classe específica é desconhecida até que seu código é executado. Nesse caso, você deve declarar a variável de objeto com o `Object` tipo de dados. Isso cria uma referência geral para qualquer tipo de objeto, e a classe específica é atribuída em tempo de execução. Isso é chamado de *ligação tardia*. A associação tardia exige tempo adicional de execução. Ela também limita seu código para os métodos e propriedades da classe que mais recentemente atribuídos a ele. Isso pode causar erros de tempo de execução se seu código tentar acessar membros de uma classe diferente.  
  
 Quando você conhece a classe específica em tempo de compilação, você deve declarar a variável de objeto para ser daquela classe. Isso é chamado de *vinculação inicial*. Associação antecipada melhora o desempenho e garante a seu código de acesso a todos os métodos e propriedades da classe específica. Nas declarações de exemplo anteriores, se a variável `objA` usa somente objetos da classe <xref:System.Windows.Forms.Label?displayProperty=fullName>, você deve especificar `As System.Windows.Forms.Label` na sua declaração.</xref:System.Windows.Forms.Label?displayProperty=fullName>  
  
### <a name="advantages-of-early-binding"></a>Vantagens da associação inicial  
 Declarar uma variável de objeto como uma classe específica dá várias vantagens:  
  
-   Verificação de tipo automática  
  
-   A garantia de acesso a todos os membros da classe específica  
  
-   Suporte do Microsoft IntelliSense no Editor de códigos  
  
-   Melhor legibilidade do seu código  
  
-   Menos erros no seu código  
  
-   Erros pegos em tempo de compilação, em vez de tempo de execução  
  
-   Execução de código mais rápida  
  
## <a name="access-to-object-variable-members"></a>Acesso aos membros das variáveis objeto  
 Quando `Option Strict` está ativado `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada. O exemplo a seguir ilustra essa situação.  
  
```  
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
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object>classe em si, que não inclui o `Left` propriedade.</xref:System.Object> Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label>classe o <xref:System.Windows.Forms>namespace.</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label>  
  
## <a name="flexibility-of-object-variables"></a>Flexibilidade de variáveis de objeto  
 Ao trabalhar com objetos em uma hierarquia de herança, você tem a opção de qual classe usar para declarar as variáveis de objeto. Fazendo a escolha, você deve equilibrar a flexibilidade de atribuição de objeto contra o acesso a membros de uma classe. Por exemplo, considere a hierarquia de herança que leva para o <xref:System.Windows.Forms.Form?displayProperty=fullName>classe:</xref:System.Windows.Forms.Form?displayProperty=fullName>  
  
 <xref:System.Object></xref:System.Object>  
  
 ``<xref:System.ComponentModel.Component></xref:System.ComponentModel.Component>  
  
 ``<xref:System.Windows.Forms.Control></xref:System.Windows.Forms.Control>  
  
 ``<xref:System.Windows.Forms.ScrollableControl></xref:System.Windows.Forms.ScrollableControl>  
  
 ``<xref:System.Windows.Forms.ContainerControl></xref:System.Windows.Forms.ContainerControl>  
  
 ``<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>  
  
 Suponha que seu aplicativo define uma classe de formulário chamada `specialForm`, que herda da classe <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form> Você pode declarar uma variável de objeto refere-se especificamente ao `specialForm`, como mostra o exemplo a seguir.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 A declaração no exemplo anterior limita a variável `nextForm` para objetos da classe `specialForm`, mas também deixa todos os métodos e propriedades de `specialForm` para `nextForm`, assim como todos os membros de todas as classes do qual `specialForm` herda.  
  
 Você pode fazer uma variável de objeto mais geral declarando-a para ser do tipo <xref:System.Windows.Forms.Form>, como mostra o exemplo a seguir.</xref:System.Windows.Forms.Form>  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 A declaração no exemplo anterior permite designar qualquer formulário em seu aplicativo para `anyForm`. No entanto, embora `anyForm` pode acessar todos os membros da classe <xref:System.Windows.Forms.Form>, ele não pode usar qualquer um dos métodos adicionais ou propriedades definidas para formulários específicos como `specialForm`.</xref:System.Windows.Forms.Form>  
  
 Todos os membros de uma classe base estão disponíveis para as classes derivadas, mas os membros adicionais de uma classe derivada não estão disponíveis para a classe base.  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [Como: acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Novo operador](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
