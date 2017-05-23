---
title: Propriedades (Visual Basic) autoimplementadas | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties, auto-implemented [Visual Basic]
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 812ef1d54e5f574dbb136f14718aa7a193a299df
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="auto-implemented-properties-visual-basic"></a>Propriedades autoimplementadas (Visual Basic)
*Propriedades autoimplementadas* permitem que você especificar uma propriedade de uma classe rapidamente sem precisar escrever código para `Get` e `Set` a propriedade. Quando você escreve o código para uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo particular para armazenar a variável de propriedade, além de criar associado `Get` e `Set` procedimentos.  
  
 Com as propriedades implementadas automaticamente, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha. O exemplo a seguir mostra três declarações de propriedade.  
  
 [!code-vb[VbVbalrAutoImplementedProperties n º&1;](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Uma propriedade autoimplementadas é equivalente a uma propriedade para a qual o valor da propriedade é armazenado em um campo particular. O exemplo de código a seguir mostra uma propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties n º&5;](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 O exemplo de código a seguir mostra o código equivalente no exemplo anterior de propriedades implementadas automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties n º&2;](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 O código a seguir mostram como implementar propriedades somente leitura:  
  
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
  
 Você pode atribuir a propriedade com expressões de inicialização conforme mostrado no exemplo, ou você pode atribuir às propriedades no construtor do tipo recipiente.  Você pode atribuir aos campos de apoio de propriedades somente leitura a qualquer momento.  
  
## <a name="backing-field"></a>Campo de backup  
 Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo privado ocultado chamado de *campo de backup* para conter o valor da propriedade. O nome do campo de backup é o nome da propriedade autoimplementadas precedido por um sublinhado (_). Por exemplo, se você declarar uma propriedade autoimplementadas denominada `ID`, o campo de backup é chamado `_ID`. Se você incluir um membro da sua classe também é chamado `_ID`, gerar um conflito de nomeação e Visual Basic relata um erro do compilador.  
  
 O campo de backup também tem as seguintes características:  
  
-   O modificador de acesso para o campo de backup é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferente, como `Public`.  
  
-   Se a propriedade é marcada como `Shared`, o campo de suporte também é compartilhado.  
  
-   Atributos especificados para a propriedade não se aplicam ao campo existente.  
  
-   O campo de backup pode ser acessado de código dentro da classe e de ferramentas de depuração, como a janela de observação. No entanto, o campo existente não mostrar em uma lista de conclusão de palavras do IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializando uma propriedade autoimplementadas  
 Qualquer expressão que pode ser usado para inicializar um campo é válido para inicializar uma propriedade implementada automaticamente. Quando você inicializar uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade. Os exemplos de código a seguir mostram algumas propriedades implementadas automaticamente que incluem valores iniciais.  
  
 [!code-vb[VbVbalrAutoImplementedProperties n º&3;](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Você não pode inicializar uma propriedade autoimplementadas que seja membro de um `Interface`, ou que está marcado como `MustOverride`.  
  
 Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, você só pode inicializar a propriedade implementada automaticamente se ele está marcado como `Shared`.  
  
 Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar limites de matriz explícita. No entanto, você pode fornecer um valor usando um inicializador de matriz, como mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties n º&4;](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definições de propriedade que exigem uma sintaxe padrão  
 Propriedades autoimplementadas são convenientes e oferecer suporte a muitos cenários de programação. No entanto, há situações nas quais você não pode usar uma propriedade implementada automaticamente e deve usar o padrão, ou *expandido*, sintaxe de propriedade.  
  
 Você deve usar sintaxe de definição de propriedade expandido se você quiser fazer qualquer um destes procedimentos:  
  
-   Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar os valores de entrada no `Set` procedimento. Por exemplo, você talvez queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.  
  
-   Especifique diferente acessibilidade para o `Get` e `Set` procedimento. Por exemplo, você talvez queira fazer a `Set` procedimento `Private` e `Get` procedimento `Public`.  
  
-   Criar propriedades `WriteOnly`.  
  
-   Usar propriedades parametrizadas (incluindo `Default` propriedades). Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade, ou especifiquem parâmetros adicionais para o `Set` procedimento.  
  
-   Colocar um atributo em um campo existente ou alterar o nível de acesso de campo existente.  
  
-   Fornece comentários XML para o campo existente.  
  
## <a name="expanding-an-auto-implemented-property"></a>Expandindo uma propriedade autoimplementadas  
 Se você precisar converter uma propriedade implementada automaticamente a uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` procedimentos e `End Property` declaração da propriedade. O código é gerado se você colocar o cursor em uma linha em branco seguinte o `Property` instrução, digite um `G` (para `Get`) ou um `S` (para `Set`) e pressione ENTER. Editor de código do Visual Basic gera automaticamente o `Get` ou `Set` procedimento para propriedades somente leitura e somente gravação quando você pressiona ENTER ao final de uma `Property` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)   
 [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Somente leitura](../../../../visual-basic/language-reference/modifiers/readonly.md)   
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

