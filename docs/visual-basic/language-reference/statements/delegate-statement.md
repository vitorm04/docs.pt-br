---
title: "Instrução delegate | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
dev_langs:
- VB
helpviewer_keywords:
- delegate keyword
- Delegate statement
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
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
ms.openlocfilehash: 9ac9e28c82f8a6b5a9c1398961d831c956a649e0
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-statement"></a>Instrução Delegate
Usada para declarar um delegado. Um delegado é um tipo de referência que se refere a um `Shared` método de um tipo ou para um método de instância de um objeto. Qualquer procedimento com correspondência de parâmetro e tipos de retorno pode ser usado para criar uma instância desta classe delegate. O procedimento pode posteriormente ser invocado por meio da instância de delegado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attrlist`|Opcional. Lista de atributos que se aplicam a este delegado. Vários atributos são separados por vírgulas. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").|  
|`accessmodifier`|Opcional. Especifica qual código pode acessar o delegado. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md). Qualquer código que pode acessar o elemento que declara o delegado pode acessá-lo.<br />-   [Protegido por](../../../visual-basic/language-reference/modifiers/protected.md). Somente o código dentro da classe do delegado ou uma classe derivada pode acessá-lo.<br />-   [Amigo](../../../visual-basic/language-reference/modifiers/friend.md). Somente o código dentro do mesmo assembly pode acessar o delegado.<br />-   [Particular](../../../visual-basic/language-reference/modifiers/private.md). Somente o código dentro do elemento que declara o delegado pode acessá-lo.<br /><br /> Você pode especificar `Protected Friend` para habilitar o acesso a partir do código na classe do delegado, uma classe derivada ou o mesmo assembly.|  
|`Shadows`|Opcional. Indica que esse delegado redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível de dentro da classe derivada que o sombreia, com exceção de onde o elemento sombreamento é inacessível. Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento da classe base em vez disso.|  
|`Sub`|Opcional, mas o `Sub` ou `Function` deve aparecer. Declara esse procedimento como um delegado `Sub` procedimento que não retorna um valor.|  
|`Function`|Opcional, mas o `Sub` ou `Function` deve aparecer. Declara esse procedimento como um delegado `Function` procedimento que retorna um valor.|  
|`name`|Necessário. Nome do tipo de delegado; segue as convenções de nomenclatura de variável padrão.|  
|`typeparamlist`|Opcional. Lista de parâmetros de tipo para este delegado. Vários parâmetros de tipo são separados por vírgulas. Opcionalmente, cada parâmetro de tipo pode ser declarado variante usando `In` e `Out` modificadores genéricos. Você deve colocar o [lista tipo](../../../visual-basic/language-reference/statements/type-list.md) entre parênteses e conectá-lo com o `Of` palavra-chave.|  
|`parameterlist`|Opcional. Lista de parâmetros que são passados para o procedimento quando é chamado. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`type`|Necessário se você especificar uma `Function` procedimento. Tipo de dados do valor de retorno.|  
  
## <a name="remarks"></a>Comentários  
 O `Delegate` instrução define os tipos de parâmetro e retorno de uma classe de delegado. Qualquer procedimento com parâmetros e tipos de retorno correspondentes pode ser usado para criar uma instância desta classe delegate. O procedimento pode posteriormente ser invocado por meio de instância delegate, chamando o delegado `Invoke` método.  
  
 Delegados podem ser declarados no namespace, módulo, classe ou nível de estrutura, mas não em um procedimento.  
  
 Cada classe delegate define um construtor que é passado a especificação de um método do objeto. Um argumento para o construtor delegado deve ser uma referência a um método ou uma expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 O tipo de tempo de compilação do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura de classe delegate. O `methodname` pode ser um método compartilhado ou um método de instância. O `methodname` não é opcional, mesmo se você criar um delegado para o método padrão da classe.  
  
 Para especificar uma expressão lambda, use a seguinte sintaxe:  
  
 `Function`([`parm` As `type`, `parm2` As `type2`, ...])`expression`  
  
 A assinatura da função deve corresponder do tipo delegado. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Para obter mais informações sobre delegados, consulte [delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Delegate` declaração para declarar um delegado para operar em dois números e retornar um número. O `DelegateTest` método obtém uma instância de um delegado desse tipo e usa-o para operar em pares de números.  
  
 [!code-vb[VbVbalrDelegates&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [De](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
