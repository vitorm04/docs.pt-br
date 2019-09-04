---
title: Propriedades autoimplementadas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: f2e25c7bcd3556f93dfedee7aa8e49bb14888123
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254027"
---
# <a name="auto-implemented-properties-visual-basic"></a>Propriedades autoimplementadas (Visual Basic)
*Propriedades autoimplementadas* permitem que você especifique uma propriedade de uma classe rapidamente sem a necessidade de escrever código para as propriedades `Get` e `Set` . uando você escreve código criando uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo *private* para armazenar a variável de propriedade, além de criar os procedimentos `Get` e `Set` associados.  
  
 Com propriedades implementadas automaticamente, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha. O exemplo a seguir mostra três declarações de propriedade.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Uma propriedade implementada automaticamente é equivalente a uma propriedade para a qual o valor da propriedade é armazenado em um campo particular. O exemplo de código a seguir mostra uma propriedade implementada automaticamente.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 O exemplo de código a seguir mostra o código equivalente para o exemplo de propriedade implementada automaticamente anterior.  
  
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
  
 Você pode atribuir a propriedade com expressões de inicialização, conforme mostrado no exemplo, ou você pode atribuir às propriedades do construtor do tipo recipiente.  Você pode atribuir aos campos de backup das propriedades ReadOnly a qualquer momento.  
  
## <a name="backing-field"></a>Campo de apoio  
 Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado o *campo de support* para conter o valor da propriedade. O nome do campo de suporte é o nome da propriedade implementada automaticamente precedido por um sublinhado (_). Por exemplo, se você declarar uma propriedade implementada automaticamente denominada `ID`, o campo de suporte é denominado `_ID`. Se você incluir um membro da sua classe que também é chamado `_ID`, isso produzirá um conflito de nomeação e o Visual Basic vai relatar um erro de compilação.  
  
 O campo de suporte também tem as seguintes características:  
  
- O modificador de acesso para o campo de backup `Private`é sempre, mesmo quando a própria propriedade tem um nível de acesso diferente `Public`, como.  
  
- Se a propriedade estiver marcada como `Shared`, o campo de backup também será compartilhado.  
  
- Os atributos especificados para a propriedade não se aplicam ao campo de backup.  
  
- O campo de suporte pode ser acessado do código dentro da classe e de ferramentas de depuração, como a janela de inspeção. No entanto, o campo de suporte não aparece na lista de conclusão do IntelliSense word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializando uma propriedade implementada automaticamente  
 Qualquer expressão que pode ser usada para inicializar um campo é válida para a inicialização de uma propriedade implementada automaticamente. Quando você Inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para `Set` o procedimento para a propriedade. Os exemplos de código a seguir mostram algumas propriedades implementadas automaticamente que incluem valores iniciais.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Não é possível inicializar uma propriedade implementada automaticamente que seja membro de um `Interface`ou um que esteja marcado como `MustOverride`.  
  
 Ao declarar uma propriedade autoimplementada como membro de um `Structure`, você só poderá inicializar a propriedade autoimplementada se ela estiver marcada como. `Shared`  
  
 Quando você declara uma propriedade implementada automaticamente como uma matriz, não é possível especificar limites de matriz explícitos. No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definições de propriedade que exigem sintaxe padrão  
 As propriedades implementadas automaticamente são convenientes e dão suporte a muitos cenários de programação. No entanto, há situações em que você não pode usar uma propriedade autoimplementada e, em vez disso, usar a sintaxe de propriedade Standard ou *Expanded*.  
  
 Você precisa usar a sintaxe de definição de propriedade expandida se desejar fazer um dos seguintes:  
  
- Adicione código ao `Get` procedimento ou `Set` de uma propriedade, como código para `Set` validar os valores de entrada no procedimento. Por exemplo, talvez você queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.  
  
- Especifique a acessibilidade diferente para `Get` o `Set` procedimento e. Por exemplo, talvez você queira fazer `Set` o procedimento `Private` e o `Get` procedimento `Public`.  
  
- Crie propriedades que são `WriteOnly`.  
  
- Use propriedades parametrizadas (incluindo `Default` Propriedades). Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade ou para especificar parâmetros adicionais para o `Set` procedimento.  
  
- Coloque um atributo no campo de apoio ou altere o nível de acesso do campo de backup.  
  
- Forneça comentários XML para o campo de backup.  
  
## <a name="expanding-an-auto-implemented-property"></a>Expandindo uma propriedade implementada automaticamente  
 Se você precisar converter uma propriedade implementada automaticamente em uma propriedade expandida que contém um `Get` procedimento `Set` ou, o editor de código Visual Basic poderá gerar automaticamente `Get` os procedimentos e `Set` `End Property`instrução para a propriedade. O código será gerado se você colocar o cursor em uma linha em branco após `Property` a instrução, digite `G` um ( `Get`para) ou `S` um ( `Set`para) e pressione Enter. O editor de código Visual Basic gera automaticamente `Get` o `Set` procedimento ou para propriedades somente leitura e somente gravação quando você pressiona Enter no final de uma `Property` instrução.  
  
## <a name="see-also"></a>Consulte também

- [Como: Declare e chame uma propriedade padrão em Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
