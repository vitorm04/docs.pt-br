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
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656078"
---
# <a name="property-procedures-visual-basic"></a>Procedimentos de propriedade (Visual Basic)
Um procedimento de propriedade é uma série de instruções do Visual Basic que manipulam uma propriedade personalizada em um módulo, classe ou estrutura. Procedimentos de propriedade são também conhecidos como *acessadores de propriedade*.  
  
 Visual Basic fornece para os procedimentos de propriedade a seguir:  
  
-   Um `Get` procedimento retorna o valor de uma propriedade. Ele é chamado quando você acessa a propriedade em uma expressão.  
  
-   Um `Set` procedimento define uma propriedade com um valor, incluindo uma referência de objeto. Ele é chamado quando você atribui um valor à propriedade.  
  
 Você geralmente define procedimentos de propriedade em pares, usando o `Get` e `Set` instruções, mas você pode definir um procedimento sozinho se a propriedade é somente leitura ([obter instrução](../../../../visual-basic/language-reference/statements/get-statement.md)) ou somente gravação ([definido Instrução](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Você pode omitir o `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente. Para obter mais informações, consulte [Propriedades autoimplementadas](./auto-implemented-properties.md).  
  
 Você pode definir propriedades em classes, estruturas e módulos. As propriedades são `Public` por padrão, que significa que você pode chamá-los de qualquer lugar no seu aplicativo que possa acessar o recipiente da propriedade.  
  
 Para obter uma comparação entre propriedades e variáveis, consulte [diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A propriedade em si é definida por um bloco de código entre as [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução. Dentro deste bloco, cada procedimento de propriedade aparece como um bloco interno incluído dentro de uma instrução de declaração (`Get` ou `Set`) e a correspondência `End` declaração.  
  
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
  
 O `Modifiers` pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento, bem como se a propriedade é somente leitura ou somente gravação. O `AccessLevel` no `Get` ou `Set` procedimento pode ser qualquer nível que seja mais restritivo do que o nível de acesso especificado para a propriedade em si. Para obter mais informações, consulte [declaração de propriedade](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Um tipo de dados e o nível de acesso principal são definidos no `Property` instrução, não nos procedimentos de propriedade. Uma propriedade pode ter apenas um tipo de dados. Por exemplo, você não pode definir uma propriedade para armazenar um `Decimal` valor mas recuperar um `Double` valor.  
  
### <a name="access-level"></a>Nível de acesso  
 No entanto, você pode definir um nível de acesso principal para uma propriedade e restringir ainda mais o nível de acesso em um dos seus procedimentos de propriedade. Por exemplo, você pode definir um `Public` propriedade e, em seguida, definir uma `Private Set` procedimento. O `Get` procedimento permanece `Public`. Você pode alterar o nível de acesso em apenas um dos procedimentos de propriedade e só pode torná-lo mais restritivo do que o nível de acesso principal. Para obter mais informações, consulte [como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Declaração de parâmetro  
 Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md), exceto que o mecanismo de passagem deve ser `ByVal`.  
  
 A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração. A sintaxe para especificar um valor padrão é da seguinte maneira:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Valor de propriedade  
 Em um `Get` procedimento, o valor de retorno é fornecido para a expressão de chamada como o valor da propriedade.  
  
 Em um `Set` procedimento, o novo valor da propriedade é passado para o parâmetro do `Set` instrução. Se você declarar explicitamente um parâmetro, declare-o com o mesmo tipo de dados da propriedade. Se você não declarar um parâmetro, o compilador usa o parâmetro implícito `Value` representar o novo valor a ser atribuído à propriedade.  
  
## <a name="calling-syntax"></a>A sintaxe de chamada  
 Você chama um procedimento de propriedade implicitamente fazendo referência à propriedade. Use o nome da propriedade da mesma maneira que você usaria o nome de uma variável, exceto que você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, opcionalmente, você pode omitir os parênteses.  
  
 A sintaxe para uma chamada implícita para um `Set` procedimento é o seguinte:  
  
 `propertyname[(argumentlist)] = expression`  
  
 A sintaxe para uma chamada implícita para um `Get` procedimento é o seguinte:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 A propriedade a seguir armazena um nome completo como dois nomes constituintes, o nome e o sobrenome. Quando o código de chamada lê `fullName`, o `Get` procedimento combina as duas partes e retorna o nome completo. Quando o código de chamada atribui um novo nome completo, o `Set` procedimento tenta dividi-lo em duas partes. Se ele não encontrar um espaço, ele armazena como o nome.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 O exemplo a seguir mostra chamadas típicas para os procedimentos de propriedade `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)  
 [Como criar uma propriedade](./how-to-create-a-property.md)  
 [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)  
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)  
 Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
