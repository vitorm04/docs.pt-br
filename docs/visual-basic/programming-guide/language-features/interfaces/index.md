---
title: Interfaces (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c26bb7322064d0b8cdf733e74f8b37e81b1e620c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="interfaces-visual-basic"></a>Interfaces (Visual Basic)
As *interfaces* definem as propriedades, os métodos e os eventos que as classes podem implementar. As interfaces permitem definir as funcionalidades como pequenos grupos de propriedades, de métodos e de eventos estreitamente relacionados. Isso reduz os problemas de compatibilidade, uma vez que é possível desenvolver implementações avançadas para as interfaces sem arriscar o código existente. Você pode adicionar novas funcionalidades a qualquer momento desenvolvendo interfaces e implementações adicionais.  
  
 Há vários outros motivos pelos quais você possa querer usar interfaces em vez da herança de classe:  
  
-   As interfaces são mais adequadas para situações em que os aplicativos exigem muitos tipos de objeto possivelmente não relacionados para fornecer determinadas funcionalidades.  
  
-   As interfaces são mais flexíveis que as classes base, uma vez que é possível definir uma única implementação que pode implementar várias interfaces.  
  
-   As interfaces são mais adequadas em situações em que você não precisa herdar a implementação de uma classe base.  
  
-   As interfaces são úteis quando você não pode usar herança de classe. Por exemplo, as estruturas não podem herdar de classes, mas podem implementar interfaces.  
  
## <a name="declaring-interfaces"></a>Declarando interfaces  
 As definições de interface são colocadas entre as instruções `Interface` e `End Interface`. Após a instrução `Interface`, você pode adicionar uma instrução `Inherits` opcional que lista uma ou mais interfaces herdadas. As instruções `Inherits` devem preceder todas as outras instruções nos comentários de exceção de declaração. As instruções restantes na definição da interface devem ser as instruções `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure` e `Enum`. As interfaces não podem conter código de implementação nem instruções associadas ao código de implementação, como `End Sub` ou `End Property`.  
  
 Em um namespace, as instruções de interface são `Friend` por padrão, mas também podem ser declaradas explicitamente como `Public` ou `Friend`. As interfaces definidas em classes, em módulos, em interfaces e em estruturas são `Public` por padrão, mas também podem ser explicitamente declaradas como `Public`, `Friend`, `Protected` ou `Private`.  
  
> [!NOTE]
>  A palavra-chave `Shadows` pode ser aplicada a todos os membros de interface. A palavra-chave `Overloads` pode ser aplicada às instruções `Sub`, `Function` e `Property` declaradas em uma definição de interface. Além disso, as instruções `Property` podem ter os modificadores `Default`, `ReadOnly` ou `WriteOnly`. Nenhum dos outros modificadores (`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride` ou `Overridable`) são permitidos. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Por exemplo, o código a seguir define uma interface com uma função, uma propriedade e um evento.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a>Implementando interfaces  
 A palavra reservada `Implements` do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] é usada de duas maneiras. A instrução `Implements` significa que uma classe ou estrutura implementa uma interface. A palavra-chave `Implements` significa que um membro de classe ou um membro da estrutura implementa um membro de interface específico.  
  
### <a name="implements-statement"></a>Instrução Implements  
 Se uma classe ou estrutura implementa uma ou mais interfaces, ela deve incluir a instrução `Implements` imediatamente após a instrução `Class` ou `Structure`. A instrução `Implements` exige uma lista de interfaces separadas por vírgula a serem implementadas por uma classe. A classe ou a estrutura deve implementar todos os membros da interface usando a palavra-chave `Implements`.  
  
### <a name="implements-keyword"></a>Palavra-chave Implements  
 A palavra-chave `Implements` exige uma lista dos membros de interface separados por vírgula a serem implementados. Em geral, apenas um único membro de interface é especificado, mas você pode especificar vários membros. A especificação de um membro de interface é composta pelo nome da interface, que deve ser especificado em uma instrução implements na classe, um período e o nome da função, da propriedade ou do evento do membro a ser implementado. O nome de um membro que implementa um membro de interface pode usar qualquer identificador válido e não está limitado à convenção `InterfaceName_MethodName` usada em versões anteriores do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Por exemplo, o código a seguir mostra como declarar uma sub-rotina chamada `Sub1` que implementa um método de uma interface:  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Os tipos de parâmetro e de retorno do membro implementado devem corresponder à propriedade da interface ou à declaração do membro na interface. A maneira mais comum de implementar um elemento de uma interface é com um membro que tem o mesmo nome que a interface, conforme mostrado no exemplo anterior.  
  
 Para declarar a implementação de um método de interface, você pode usar os atributos válidos em declarações de método de instância, incluindo `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default` e `Static`. O atributo `Shared` não é válido, uma vez que define uma classe em vez de um método de instância.  
  
 Ao usar `Implements`, você também pode escrever um único método que implementa vários métodos definidos em uma interface, como no exemplo a seguir:  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Você pode usar um membro particular para implementar um membro de interface. Quando um membro particular implementa um membro de uma interface, esse membro fica disponível por meio da interface, embora não esteja disponível diretamente em variáveis de objeto para a classe.  
  
### <a name="interface-implementation-examples"></a>Exemplos de implementação de interface  
 As classes que implementam uma interface devem implementar todas as suas propriedades, métodos e eventos.  
  
 O exemplo a seguir define duas interfaces. A segunda interface, `Interface2`, herda `Interface1` e define uma propriedade e um método adicionais.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 O exemplo a seguir implementa `Interface1`, a interface definida no exemplo anterior:  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 O exemplo final implementa `Interface2`, incluindo um método herdado de `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Você pode implementar uma propriedade readonly com uma propriedade readwrite (ou seja, você não precisa declará-la como readonly na classe sendo implementada).  Implementar uma interface significa implementar pelo menos os membros que a interface declara, mas você pode oferecer mais funcionalidades, como permitir que a propriedade seja gravável.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: criando e implementando interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Fornece um procedimento detalhado que o guiará pelo processo de definição e de implementação de sua própria interface.|  
|[Variação em Interfaces Genéricas](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Discute a covariância e a contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.|
