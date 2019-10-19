---
title: Instrução delegate (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4a8260da4d2224551de71fd54f734007c7fa214f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583452"
---
# <a name="delegate-statement"></a>Instrução Delegate
Usado para declarar um delegado. Um delegado é um tipo de referência que se refere a um método `Shared` de um tipo ou a um método de instância de um objeto. Qualquer procedimento com parâmetros correspondentes e tipos de retorno pode ser usado para criar uma instância dessa classe delegate. O procedimento pode ser posteriormente invocado por meio da instância de delegado.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attrlist`|Opcional. Lista de atributos que se aplicam a este delegado. Vários atributos são separados por vírgulas. Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`" e "`>`").|  
|`accessmodifier`|Opcional. Especifica qual código pode acessar o delegado. Pode ser um dos seguintes:<br /><br /> - [público](../../../visual-basic/language-reference/modifiers/public.md). Qualquer código que possa acessar o elemento que declara o delegado pode acessá-lo.<br />-   [protegido](../../../visual-basic/language-reference/modifiers/protected.md). Somente o código dentro da classe do delegado ou de uma classe derivada pode acessá-lo.<br />-   [amigo](../../../visual-basic/language-reference/modifiers/friend.md). Somente o código dentro do mesmo assembly pode acessar o delegado.<br />- [privado](../../../visual-basic/language-reference/modifiers/private.md). Somente o código dentro do elemento que declara o delegado pode acessá-lo.<br /><br /> -  somente[Friend Protected](../../language-reference/modifiers/protected-friend.md) código dentro da classe do delegado, uma classe derivada ou o mesmo assembly podem acessar o delegado. <br />-  código[protegido somente particular](../../language-reference/modifiers/private-protected.md) dentro da classe do delegado ou em uma classe derivada no mesmo assembly pode acessar o delegado. |  
|`Shadows`|Opcional. Indica que esse delegado redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, em uma classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que o sombreia, exceto de onde o elemento de sombreamento está inacessível. Por exemplo, se um elemento `Private` sombreia um elemento de classe base, o código que não tem permissão para acessar o elemento `Private` acessa o elemento da classe base em vez disso.|  
|`Sub`|Opcional, mas `Sub` ou `Function` devem aparecer. Declara esse procedimento como um delegado `Sub` procedimento que não retorna um valor.|  
|`Function`|Opcional, mas `Sub` ou `Function` devem aparecer. Declara esse procedimento como um delegado `Function` procedimento que retorna um valor.|  
|`name`|Necessário. Nome do tipo delegado; segue as convenções padrão de nomenclatura de variável.|  
|`typeparamlist`|Opcional. Lista de parâmetros de tipo para este delegado. Vários parâmetros de tipo são separados por vírgulas. Opcionalmente, cada parâmetro de tipo pode ser declarado como Variant usando `In` e `Out` modificadores genéricos. Você deve colocar a [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) entre parênteses e apresentá-la com a palavra-chave `Of`.|  
|`parameterlist`|Opcional. Lista de parâmetros que são passados para o procedimento quando ele é chamado. Você deve colocar a [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`type`|Necessário se você especificar um procedimento de `Function`. Tipo de dados do valor de retorno.|  
  
## <a name="remarks"></a>Comentários  
 A instrução `Delegate` define o parâmetro e os tipos de retorno de uma classe delegate. Qualquer procedimento com parâmetros e tipos de retorno correspondentes pode ser usado para criar uma instância dessa classe delegate. O procedimento pode ser posteriormente invocado por meio da instância de delegado, chamando o método de `Invoke` do delegado.  
  
 Os delegados podem ser declarados no nível de namespace, módulo, classe ou estrutura, mas não dentro de um procedimento.  
  
 Cada classe de delegado define um construtor que é passado para a especificação de um método do objeto. Um argumento para o construtor delegado deve ser uma referência a um método ou uma expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 O tipo de tempo de compilação do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura da classe delegada. O `methodname` pode ser um método compartilhado ou um método de instância. O `methodname` não é opcional, mesmo se você criar um delegado para o método padrão da classe.  
  
 Para especificar uma expressão lambda, use a seguinte sintaxe:  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 A assinatura da função deve corresponder a do tipo delegado. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Para obter mais informações sobre delegados, confira [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Delegate` para declarar um delegado para operar em dois números e retornar um número. O método `DelegateTest` usa uma instância de um delegado desse tipo e a usa para operar em pares de números.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Consulte também

- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Covariância e Contravariância](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
