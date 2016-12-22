---
title: "Propriedades autoimplementadas (Visual Basic) | Microsoft Docs"
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
  - "vb.AutoProperty"
  - "vb.AutoImplementedProperty"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedades autoimplementadas [Visual Basic]"
  - "propriedades [Visual Basic], autoimplementadas"
  - "propriedades, autoimplementado [Visual Basic]"
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedades autoimplementadas (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*Propriedades autoimplementadas* permitem que você especificar uma propriedade de uma classe rapidamente sem precisar escrever código para `Get` e `Set` a propriedade.  Quando você escreve o código para uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo particular para armazenar a variável de propriedade, além de criar associado `Get` e `Set` procedimentos.  
  
 Com as propriedades implementadas automaticamente, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha.  O exemplo a seguir mostra três declarações de propriedade.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Uma propriedade autoimplementadas é equivalente a uma propriedade para o qual o valor da propriedade é armazenado em um campo particular.  O exemplo de código a seguir mostra uma propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 O exemplo de código a seguir mostra o código equivalente no exemplo anterior de propriedades implementadas automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 O código a seguir mostram a implementação de propriedades somente leitura:  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
  
```  
  
 Você pode atribuir a propriedade com expressões de inicialização conforme mostrado no exemplo, ou você pode atribuir às propriedades no construtor do tipo recipiente.  Você pode atribuir aos campos apoio de propriedades somente leitura a qualquer momento.  
  
## Campo existente  
 Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado a *campo existente* para conter o valor da propriedade.  O nome do campo de backup é o nome de propriedade autoimplementadas precedido por um sublinhado \(\_\).  Por exemplo, se você declarar uma propriedade autoimplementadas denominada `ID`, o campo existente chamado `_ID`.  Se você incluir um membro da sua classe também é denominada `_ID`, produzir um conflito de nomeação e Visual Basic relata um erro do compilador.  
  
 O campo existente também tem as seguintes características:  
  
-   O modificador de acesso para o campo existente é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferente, como `Public`.  
  
-   Se a propriedade é marcada como `Shared`, o campo existente também é compartilhado.  
  
-   Atributos especificados para a propriedade não se aplicam ao campo existente.  
  
-   O campo existente pode ser acessado de código dentro da classe e de ferramentas de depuração, como a janela de observação.  No entanto, o campo existente não mostra em uma lista de conclusão de palavras do IntelliSense.  
  
## Inicializando uma propriedade autoimplementadas  
 Qualquer expressão que pode ser usado para inicializar um campo é válido para inicializar uma propriedade implementada automaticamente.  Quando você inicializar uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade.  Os exemplos de código a seguir mostram algumas propriedades autoimplementadas que incluem valores iniciais.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Você não pode inicializar uma propriedade autoimplementadas que seja membro de um `Interface`, ou que está marcado como `MustOverride`.  
  
 Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, você só pode inicializar a propriedade implementada automaticamente se ele estiver marcado como `Shared`.  
  
 Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar limites de matriz explícita.  No entanto, você pode fornecer um valor usando um inicializador de matriz, como mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## Definições de propriedade que exigem a sintaxe padrão  
 Propriedades autoimplementadas são convenientes e oferecer suporte a muitos cenários de programação.  No entanto, há situações nas quais você não pode usar uma propriedade implementada automaticamente e deve usar o padrão, ou *expandido*, sintaxe de propriedade.  
  
 Você precisa usar a sintaxe de definição de propriedade expandido se você quiser fazer qualquer um dos seguintes:  
  
-   Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar os valores de entrada no `Set` procedimento.  Por exemplo, você talvez queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.  
  
-   Especificar diferente acessibilidade para o `Get` e `Set` procedimento.  Por exemplo, convém fazer o `Set` procedimento `Private` e o `Get` procedimento `Public`.  
  
-   Criar propriedades `WriteOnly`.  
  
-   Usar propriedades parametrizadas \(incluindo `Default` Propriedades\).  Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade, ou especifiquem parâmetros adicionais para o `Set` procedimento.  
  
-   Colocar um atributo em um campo existente ou alterar o nível de acesso do campo existente.  
  
-   Fornece comentários XML para o campo existente.  
  
## Expandindo uma propriedade autoimplementadas  
 Se você precisar converter uma propriedade implementada automaticamente a uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` procedimentos e `End Property` declaração da propriedade.  O código é gerado se você colocar o cursor em uma linha em branco seguinte a `Property` instrução, digite um `G` \(para `Get`\) ou um `S` \(para `Set`\) e pressione ENTER.  Editor de código do Visual Basic gera automaticamente o `Get` ou `Set` procedimento para propriedades somente leitura e somente gravação quando você pressiona ENTER ao final de uma `Property` instrução.  
  
## Consulte também  
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)   
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)