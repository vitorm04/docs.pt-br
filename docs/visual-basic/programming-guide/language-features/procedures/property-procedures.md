---
title: Procedimentos de propriedade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791853"
---
# <a name="property-procedures-visual-basic"></a>Procedimentos de propriedade (Visual Basic)
Um procedimento de propriedade é uma série de instruções do Visual Basic que manipulam uma propriedade personalizada em um módulo, classe ou estrutura. Procedimentos de propriedade também são conhecidos como *acessadores de propriedade*.  
  
 Visual Basic fornece para os procedimentos de propriedade a seguir:  
  
- Um `Get` procedimento retorna o valor de uma propriedade. Ele é chamado quando você acessa a propriedade em uma expressão.  
  
- Um `Set` procedimento define uma propriedade com um valor, incluindo uma referência de objeto. Ele é chamado quando você atribui um valor à propriedade.  
  
 Você geralmente define procedimentos de propriedade de pares, usando o `Get` e `Set` instruções, mas você pode definir um procedimento sozinho se a propriedade é somente leitura ([instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md)) ou somente gravação ([definido Instrução](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Você pode omitir as `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente. Para obter mais informações, consulte [Propriedades autoimplementadas](./auto-implemented-properties.md).  
  
 Você pode definir propriedades nas classes, estruturas e módulos. As propriedades são `Public` por padrão, que significa que você pode chamá-los de qualquer lugar em seu aplicativo que possa acessar o recipiente da propriedade.  
  
 Para obter uma comparação entre propriedades e variáveis, consulte [diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 Uma propriedade em si é definida por um bloco de código entre o [instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) e o `End Property` instrução. Dentro desse bloco, cada procedimento de propriedade aparece como um bloco interno incluído dentro de uma instrução de declaração (`Get` ou `Set`) e a correspondência `End` declaração.  
  
 A sintaxe para declarar uma propriedade e seus procedimentos é da seguinte maneira:  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 O `Modifiers` pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento, bem como se a propriedade é somente leitura ou somente gravação. O `AccessLevel` sobre o `Get` ou `Set` procedimento pode ser qualquer nível que é mais restritivo que o nível de acesso especificado para a propriedade em si. Para obter mais informações, consulte [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Tipo de dados da propriedade e o nível de acesso principal são definidos na `Property` instrução, não nos procedimentos de propriedade. Uma propriedade pode ter apenas um tipo de dados. Por exemplo, você não pode definir uma propriedade para armazenar um `Decimal` valor, mas recuperar um `Double` valor.  
  
### <a name="access-level"></a>Nível de acesso  
 No entanto, você pode definir um nível de acesso à entidade para uma propriedade e restringir ainda mais o nível de acesso em um dos seus procedimentos de propriedade. Por exemplo, você pode definir um `Public` propriedade e, em seguida, definir um `Private Set` procedimento. O `Get` procedimento permanece `Public`. Você pode alterar o nível de acesso em apenas um dos procedimentos de uma propriedade e somente pode torná-lo mais restritivo do que o nível de acesso principal. Para obter mais informações, confira [Como: Declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Declaração de parâmetro  
 Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md), exceto que o mecanismo de passagem deve ser `ByVal`.  
  
 A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração. A sintaxe para especificar um valor padrão é da seguinte maneira:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Valor da propriedade  
 Em um `Get` procedimento, o valor retornado é fornecido para a expressão de chamada como o valor da propriedade.  
  
 Em um `Set` procedimento, o novo valor da propriedade é passado para o parâmetro do `Set` instrução. Se você declarar explicitamente um parâmetro, você deve declará-la com o mesmo tipo de dados como a propriedade. Se você não declarar um parâmetro, o compilador usa o parâmetro implícito `Value` para representar o novo valor a ser atribuído à propriedade.  
  
## <a name="calling-syntax"></a>Sintaxe de chamada  
 Você invoca um procedimento de propriedade implicitamente fazendo referência à propriedade. Use o nome da propriedade da mesma maneira que você usaria o nome de uma variável, exceto que você deve fornecer valores para todos os argumentos que não são opcionais e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, você pode, opcionalmente, omitir os parênteses.  
  
 A sintaxe para uma chamada implícita para um `Set` procedimento é o seguinte:  
  
 `propertyname[(argumentlist)] = expression`  
  
 A sintaxe para uma chamada implícita para um `Get` procedimento é o seguinte:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 A propriedade a seguir armazena um nome completo como dois nomes constituintes, o nome e o sobrenome. Quando o código de chamada lê `fullName`, o `Get` procedimento combina as duas partes e retorna o nome completo. Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em duas partes. Se não encontrar um espaço, ele armazena tudo como o nome.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 O exemplo a seguir mostra chamadas típicas para os procedimentos de propriedade de `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como: Criar uma propriedade](./how-to-create-a-property.md)
- [Como: Chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: Declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como: Inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
- [Como: Obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
