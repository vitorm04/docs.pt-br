---
title: "Instru&#231;&#227;o Delegate | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Delegate"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave delegate"
  - "instrução Delegate"
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Delegate
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para declarar um delegado.  Um delegado é um tipo de referência que se refere a uma `Shared` método de um tipo ou a um método de instância de um objeto.   Qualquer procedimento com o parâmetro e tipos de retorno correspondentes pode ser usado para criar uma instância dessaclassede delegado.   O procedimento mais tarde, em seguida, pode ser chamado por meio de uma instância do delegado .  
  
## Sintaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attrlist`|Opcional.  Lista de atributos que aplicar a este delegado.  Diversos parâmetros são separados por vírgulas.  Você delimitar a [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes \("`<`" e "`>`"\).|  
|`accessmodifier`|Opcional.  Especifica qual código pode acessar a delegado.  Pode ser um dos seguintes:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md).  Qualquer código que pode acessar o elemento que declara o delegado pode acessá\-lo.<br />-   [Protegido por](../../../visual-basic/language-reference/modifiers/protected.md).  Somente o código dentro do delegadoda classe ou uma classe de derivada pode acessá\-lo.<br />-   [Amigo](../../../visual-basic/language-reference/modifiers/friend.md).  Somente o código dentro do mesmo assembly pode acessar a delegado.<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md).  Somente o código dentro do elemento que declara o delegado pode acessá\-lo.<br /><br /> Você pode especificar `Protected Friend` para permitir o acesso do código dentro do mesmo assembly, uma classede derivada ou o delegadoda classe.|  
|`Shadows`|Opcional.  Indica que este delegado redeclara e oculta um elemento de programação com nomes idênticos ou conjunto de elementos sobrecarregados, em uma classe base.  Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.<br /><br /> Um elemento sombreado não está disponível dentro da classe derivada que o sombreia, com exceção de onde o elemento sombreamento é inacessível.  Por exemplo, se um elemento `Private` sombreia um elemento da classe base, o código que não possui permissão para acessar o elemento `Private` acessa o elemento da classe base em vez disso.|  
|`Sub`|É opcional, mas um `Sub` ou `Function` deve ser exibido.  Esse procedimento como um delegadode declara`Sub`procedimento que retorna um valor.|  
|`Function`|É opcional, mas um `Sub` ou `Function` deve ser exibido.  Esse procedimento como um delegadode declara`Function`procedimento que retorna um valor.|  
|`name`|Necessário.  Nome do tipo delegado ; segue um padrão variável de convenções de nomenclatura.|  
|`typeparamlist`|Opcional.  Lista de parâmetros de tipo para este delegado.  Vários parâmetros de tipo são separados por vírgulas.  Opcionalmente, cada tipo de parâmetro pode ser declarada variante usando `In` e `Out` modificadores genéricos.  Você deve colocar o [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) entre parênteses e conectá\-lo com o `Of` palavra\-chave.|  
|`parameterlist`|Opcional.  Lista de parâmetros que são passados para o procedimento , quando for chamado.  Você deverá colocar o [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) entre parênteses.|  
|`type`|Necessário se você especificar um `Function` procedimento.   Tipo de dados do valor retornado.|  
  
## Comentários  
 O `Delegate` demonstrativo define o parâmetro e tipos de retorno de umaclassede delegado.    Qualquer procedimento com parâmetros e tipos de retorno correspondentes pode ser usado para criar uma instância dessaclassede delegado.   O procedimento pode posteriormente ser invocado por meio de uma instância delegado , chamando o delegadodo `Invoke` método.  
  
 Representantes podem ser declaradas com o namespace, módulo, classeou estrutura nível, mas não dentro de um procedimento.  
  
 Cada classe de delegados define um construtor que passa a especificação a um método objeto.  Um argumento para um construtor delegate deve ser uma referência a um método ou um expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` \[`expression`.\]`methodname`  
  
 O compile\-time type do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura de classe Delegate.  O `methodname` pode ser um método compartilhado ou um método de instância.  `methodname` não é opcional, mesmo se você criar um representante para o método padrão da classe.  
  
 Para especificar um expressão lambda, use a seguinte sintaxe:  
  
 `Function`\(`parm` As `type`, `parm2` As `type2`, ...\]\)`expression`  
  
 A assinatura de função deve corresponder do tipo delegate.  Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Para obter mais informações sobre delegados, consulte [Delegados](../../../visual-basic/programming-guide/language-features/delegates/delegates.md).  
  
## Exemplo  
 O exemplo a seguir usa a `Delegate`de demonstrativo para declarar um delegado para operar em dois números e retornando um número.   O `DelegateTest` método obtém uma instância de um delegado desse tipo e o usa para operar em pares de números.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## Consulte também  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Covariância e contravariância](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)