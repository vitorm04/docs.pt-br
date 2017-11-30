---
title: "Instrução Delegate"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e79a261f74cbc7aa067af63629e31bedf65d163
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-statement"></a>Instrução Delegate
Usado para declarar um delegado. Um delegado é um tipo de referência que se refere a um `Shared` método de um tipo ou a um método de instância de um objeto. Qualquer procedimento com parâmetro e retornar os tipos de correspondência pode ser usado para criar uma instância desta classe delegate. O procedimento posteriormente, em seguida, pode ser chamado por meio da instância delegada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`attrlist`|Opcional. Lista de atributos que se aplicam a este delegado. Vários atributos são separados por vírgulas. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").|  
|`accessmodifier`|Opcional. Especifica o código pode acessar o delegado. Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md). Qualquer código que pode acessar o elemento que declara o representante pode acessá-lo.<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md). Somente o código dentro da classe do representante ou uma classe derivada pode acessá-lo.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Somente o código dentro do mesmo assembly pode acessar o delegado.<br />-   [Particular](../../../visual-basic/language-reference/modifiers/private.md). Somente o código dentro do elemento que declara o representante pode acessá-lo.<br /><br /> Você pode especificar `Protected Friend` para habilitar o acesso do código na classe do representante, uma classe derivada ou do mesmo assembly.|  
|`Shadows`|Opcional. Indica que este delegado redeclara e oculta um elemento de programação com o mesmo nome, ou um conjunto de elementos sobrecarregados, em uma classe base. Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível dentro da classe derivada que sombreia, com exceção de onde o elemento sombreamento é inacessível. Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento de classe base em vez disso.|  
|`Sub`|Opcional, mas o `Sub` ou `Function` devem aparecer. Declara a esse procedimento como um delegado `Sub` procedimento que não retorna um valor.|  
|`Function`|Opcional, mas o `Sub` ou `Function` devem aparecer. Declara a esse procedimento como um delegado `Function` procedimento que retorna um valor.|  
|`name`|Necessário. Nome do tipo de delegado; segue convenções de nomenclatura de variável padrão.|  
|`typeparamlist`|Opcional. Lista de parâmetros de tipo para este delegado. Vários parâmetros de tipo são separados por vírgulas. Opcionalmente, cada parâmetro de tipo pode ser declarado variante usando `In` e `Out` modificadores genéricos. Você deve colocar o [lista tipo](../../../visual-basic/language-reference/statements/type-list.md) entre parênteses e conectá-lo com o `Of` palavra-chave.|  
|`parameterlist`|Opcional. Lista de parâmetros que são passados para o procedimento quando ele é chamado. Você deve colocar o [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`type`|Necessário se você especificar um `Function` procedimento. Tipo de dados do valor de retorno.|  
  
## <a name="remarks"></a>Comentários  
 O `Delegate` instrução define os tipos de parâmetro e retorno de uma classe delegate. Qualquer procedimento com parâmetros e tipos de retorno correspondentes pode ser usado para criar uma instância desta classe delegate. O procedimento pode depois ser invocado por meio da instância do representante, chamando o delegado `Invoke` método.  
  
 Delegados podem ser declarados no namespace, módulo, classe ou nível de estrutura, mas não dentro de um procedimento.  
  
 Cada classe de delegado define um construtor que é passado para a especificação de um método do objeto. Um argumento para o construtor delegado deve ser uma referência a um método ou uma expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 O tipo de tempo de compilação do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura da classe delegada. O `methodname` pode ser um método compartilhado ou um método de instância. O `methodname` não é opcional, mesmo se você criar um delegado para o método padrão da classe.  
  
 Para especificar uma expressão lambda, use a seguinte sintaxe:  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 A assinatura da função deve corresponder a do tipo delegado. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Para obter mais informações sobre delegados, consulte [delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Delegate` instrução para declarar um delegado para operar em dois números e retornando um número. O `DelegateTest` método usa uma instância de um representante desse tipo e o utiliza para operar em pares de números.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Covariância e Contravariância](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
