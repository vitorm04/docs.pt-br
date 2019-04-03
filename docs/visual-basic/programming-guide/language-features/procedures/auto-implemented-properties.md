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
ms.openlocfilehash: aa045dd5454819a37ad81c76d97fd3e61e7d0420
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841245"
---
# <a name="auto-implemented-properties-visual-basic"></a>Propriedades autoimplementadas (Visual Basic)
*Propriedades autoimplementadas* permitem que você especifique uma propriedade de uma classe rapidamente sem a necessidade de escrever código para as propriedades `Get` e `Set` . uando você escreve código criando uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo *private* para armazenar a variável de propriedade, além de criar os procedimentos `Get` e `Set` associados.  
  
 Com Propriedades autoimplementadas, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha. O exemplo a seguir mostra três declarações de propriedade.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Uma propriedade implementada automaticamente é equivalente a uma propriedade para o qual o valor da propriedade é armazenado em um campo particular. O exemplo de código a seguir mostra uma propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 O exemplo de código a seguir mostra o código equivalente no exemplo anterior da propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
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
  
 Você pode atribuir a propriedade com expressões de inicialização, conforme mostrado no exemplo, ou você pode atribuir às propriedades do construtor do tipo recipiente.  Você pode atribuir a campos de suporte das propriedades somente leitura a qualquer momento.  
  
## <a name="backing-field"></a>Campo de suporte  
 Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado o *campo de support* para conter o valor da propriedade. O nome do campo de suporte é o nome da propriedade implementada automaticamente precedido por um sublinhado (_). Por exemplo, se você declarar uma propriedade implementada automaticamente denominada `ID`, o campo de suporte é denominado `_ID`. Se você incluir um membro da sua classe que também é chamado `_ID`, isso produzirá um conflito de nomeação e o Visual Basic vai relatar um erro de compilação.  
  
 O campo de suporte também tem as seguintes características:  
  
-   O modificador de acesso para o campo de suporte é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferentes, como `Public`.  
  
-   Se a propriedade é marcada como `Shared`, o campo de suporte também é compartilhado.  
  
-   Atributos especificados para a propriedade não se aplicam ao campo de suporte.  
  
-   O campo de suporte pode ser acessado do código dentro da classe e de ferramentas de depuração, como a janela de inspeção. No entanto, o campo de suporte não aparece na lista de conclusão do IntelliSense word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializando uma propriedade implementada automaticamente  
 Qualquer expressão que pode ser usada para inicializar um campo é válida para a inicialização de uma propriedade implementada automaticamente. Quando você inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade. Os exemplos de código a seguir mostram algumas propriedades autoimplementadas que incluem valores iniciais.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Você não pode inicializar uma propriedade autoimplementada que é um membro de um `Interface`, ou que está marcado como `MustOverride`.  
  
 Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, você só pode inicializar a propriedade implementada automaticamente se ele está marcado como `Shared`.  
  
 Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar os limites de matriz explícita. No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definições de propriedade que exigem a sintaxe padrão  
 Propriedades autoimplementadas são convenientes e dar suporte a muitos cenários de programação. No entanto, há situações em que você não pode usar uma propriedade implementada automaticamente e em vez disso, deve usar o padrão, ou *expandido*, sintaxe de propriedade.  
  
 Você precisa usar a sintaxe de definição de propriedade expandido se você quiser fazer qualquer um dos seguintes:  
  
-   Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar valores de entrada no `Set` procedimento. Por exemplo, você talvez queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.  
  
-   Especificar a acessibilidade diferente para o `Get` e `Set` procedimento. Por exemplo, você talvez queira fazer a `Set` procedimento `Private` e o `Get` procedimento `Public`.  
  
-   Criar propriedades que são `WriteOnly`.  
  
-   Usar propriedades parametrizadas (incluindo `Default` propriedades). Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade, ou para especificar parâmetros adicionais para o `Set` procedimento.  
  
-   Colocar um atributo no campo de suporte, ou alterar o nível de acesso do campo de backup.  
  
-   Fornece comentários XML para o campo de suporte.  
  
## <a name="expanding-an-auto-implemented-property"></a>Expandindo uma propriedade implementada automaticamente  
 Se você precisar converter uma propriedade implementada automaticamente a uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` eprocedimentos`End Property`instrução para a propriedade. O código é gerado se você colocar o cursor em uma linha em branco após o `Property` instrução, digite um `G` (para `Get`) ou uma `S` (para `Set`) e pressione ENTER. Editor de código do Visual Basic gera automaticamente a `Get` ou `Set` procedimento para propriedades somente leitura e somente gravação ao pressionar ENTER no final de um `Property` instrução.  
  
## <a name="see-also"></a>Consulte também

- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
