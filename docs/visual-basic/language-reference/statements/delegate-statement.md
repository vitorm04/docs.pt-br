---
title: Instrução Delegate
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 662d2c3c0767adfe406e0a6f1b1e6dccd704e795
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354068"
---
# <a name="delegate-statement"></a>Instrução Delegate
Used to declare a delegate. A delegate is a reference type that refers to a `Shared` method of a type or to an instance method of an object. Any procedure with matching parameter and return types can be used to create an instance of this delegate class. The procedure can then later be invoked by means of the delegate instance.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attrlist`|Opcional. List of attributes that apply to this delegate. Multiple attributes are separated by commas. You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").|  
|`accessmodifier`|Opcional. Specifies what code can access the delegate. Can be one of the following:<br /><br /> - [Public](../../../visual-basic/language-reference/modifiers/public.md). Any code that can access the element that declares the delegate can access it.<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md). Only code within the delegate's class or a derived class can access it.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Only code within the same assembly can access the delegate.<br />- [Private](../../../visual-basic/language-reference/modifiers/private.md). Only code within the element that declares the delegate can access it.<br /><br /> - [Protected Friend](../../language-reference/modifiers/protected-friend.md) Only code within the delegate's class, a derived class, or the same assembly can access the delegate. <br />- [Private Protected](../../language-reference/modifiers/private-protected.md) Only code within the delegate's class or in a derived class in the same assembly can access the delegate. |  
|`Shadows`|Opcional. Indicates that this delegate redeclares and hides an identically named programming element, or set of overloaded elements, in a base class. You can shadow any kind of declared element with any other kind.<br /><br /> A shadowed element is unavailable from within the derived class that shadows it, except from where the shadowing element is inaccessible. For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.|  
|`Sub`|Optional, but either `Sub` or `Function` must appear. Declares this procedure as a delegate `Sub` procedure that does not return a value.|  
|`Function`|Optional, but either `Sub` or `Function` must appear. Declares this procedure as a delegate `Function` procedure that returns a value.|  
|`name`|Necessário. Name of the delegate type; follows standard variable naming conventions.|  
|`typeparamlist`|Opcional. List of type parameters for this delegate. Multiple type parameters are separated by commas. Optionally, each type parameter can be declared variant by using `In` and `Out` generic modifiers. You must enclose the [Type List](../../../visual-basic/language-reference/statements/type-list.md) in parentheses and introduce it with the `Of` keyword.|  
|`parameterlist`|Opcional. List of parameters that are passed to the procedure when it is called. You must enclose the [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) in parentheses.|  
|`type`|Required if you specify a `Function` procedure. Data type of the return value.|  
  
## <a name="remarks"></a>Comentários  
 The `Delegate` statement defines the parameter and return types of a delegate class. Any procedure with matching parameters and return types can be used to create an instance of this delegate class. The procedure can then later be invoked by means of the delegate instance, by calling the delegate's `Invoke` method.  
  
 Delegates can be declared at the namespace, module, class, or structure level, but not within a procedure.  
  
 Cada classe de delegado define um construtor que é passado para a especificação de um método do objeto. Um argumento para o construtor delegado deve ser uma referência a um método ou uma expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 O tipo de tempo de compilação do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura da classe delegada. O `methodname` pode ser um método compartilhado ou um método de instância. O `methodname` não é opcional, mesmo se você criar um delegado para o método padrão da classe.  
  
 Para especificar uma expressão lambda, use a seguinte sintaxe:  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 A assinatura da função deve corresponder a do tipo delegado. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Para obter mais informações sobre delegados, confira [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemplo  
 The following example uses the `Delegate` statement to declare a delegate for operating on two numbers and returning a number. The `DelegateTest` method takes an instance of a delegate of this type and uses it to operate on pairs of numbers.  
  
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
