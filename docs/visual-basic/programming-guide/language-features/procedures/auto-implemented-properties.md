---
title: Propriedades autoimplementadas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656302"
---
# <a name="auto-implemented-properties-visual-basic"></a>Propriedades autoimplementadas (Visual Basic)
*Propriedades autoimplementadas* permitem que você especifique uma propriedade de uma classe rapidamente sem a necessidade de escrever código para as propriedades `Get` e `Set`. Quando você escreve código criando uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo *private* para armazenar a variável de propriedade, além de criar os procedimentos `Get` e `Set` associados.  
  
 Com Propriedades autoimplementadas, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha. O exemplo a seguir mostra três declarações de propriedade.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Uma propriedade implementada automaticamente é equivalente a uma propriedade para o qual o valor da propriedade é armazenado em um campo particular. O exemplo de código a seguir mostra uma propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 O exemplo de código a seguir mostra o código equivalente para o exemplo anterior da propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 O código a seguir mostra como implementar propriedades somente leitura:  
  
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
  
 Você pode atribuir a propriedade com expressões de inicialização, conforme mostrado no exemplo, ou você pode atribuir às propriedades do construtor do tipo recipiente.  Você pode atribuir aos campos de backup propriedades somente leitura a qualquer momento.  
  
## <a name="backing-field"></a>Campo de backup  
 Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado o *campo de backup* para conter o valor da propriedade. O nome do campo de backup é o nome da propriedade implementada automaticamente precedido por um *underline* (_). Por exemplo, se você declarar uma propriedade implementada automaticamente denominada `ID`, o campo de backup é denominado `_ID`. Se você incluir um membro da sua classe que também é chamado `_ID`, isso irá produzir um conflito de nomeação e o Visual Basic vai relatar um erro de compilação.  
  
 O campo de backup também tem as seguintes características:  
  
-   O modificador de acesso para o campo de backup é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferentes, como `Public`.  
  
-   Se a propriedade é marcada como `Shared`, o campo de reforço também é compartilhado.  
  
-   Atributos especificados para a propriedade não se aplicam ao campo de backup.  
  
-   O campo de backup pode ser acessado do código dentro da classe e de ferramentas de depuração, como a janela de inspeção. No entanto, o campo de backup não aparece na lista de sugestões do IntelliSense word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializando uma propriedade implementada automaticamente  
 Qualquer expressão que pode ser usada para inicializar um campo é válida para a inicialização de uma propriedade implementada automaticamente. Quando você inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade. Os exemplos de código a seguir mostram algumas propriedades autoimplementadas que incluem valores iniciais.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Não é possível inicializar uma propriedade implementada automaticamente que é um membro de um `Interface`, ou que está marcado como `MustOverride`.  
  
 Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, só é possível inicializar a propriedade implementada automaticamente, se ele está marcado como `Shared`.  
  
 Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar limites de matriz explícita. No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definições de propriedade que exigem a sintaxe padrão  
 Propriedades autoimplementadas são convenientes e dar suporte a vários cenários de programação. No entanto, há situações nas quais você não pode usar uma propriedade implementada automaticamente e deve usar o padrão, ou *expandido*, sintaxe de propriedade.  
  
 Você deve usar a sintaxe de definição de propriedade expandido se quiser fazer qualquer um dos seguintes:  
  
-   Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar valores de entrada no `Set` procedimento. Por exemplo, convém verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.  
  
-   Especificar diferente acessibilidade para o `Get` e `Set` procedimento. Por exemplo, talvez você queira fazer a `Set` procedimento `Private` e `Get` procedimento `Public`.  
  
-   Criar propriedades `WriteOnly`.  
  
-   Usar propriedades com parâmetros (incluindo `Default` propriedades). Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade ou para especificar parâmetros adicionais para o `Set` procedimento.  
  
-   Coloque um atributo em um campo existente ou alterar o nível de acesso de campo existente.  
  
-   Fornece comentários XML para o campo de backup.  
  
## <a name="expanding-an-auto-implemented-property"></a>Expandindo uma propriedade implementada automaticamente  
 Se você precisar converter uma propriedade implementada automaticamente para uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` procedimentos e `End Property`instrução para a propriedade. O código é gerado se você colocar o cursor em uma linha em branco após o `Property` instrução, digite um `G` (para `Get`) ou um `S` (para `Set`) e pressione ENTER. Editor de código do Visual Basic gera automaticamente o `Get` ou `Set` procedimento para propriedades somente leitura e gravação ao pressionar ENTER no final de um `Property` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
