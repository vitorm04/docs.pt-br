---
title: "Sobrecarregado propriedades e métodos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 6f379f04ca9b75161baf2bf2c33e87f05a9edf97
ms.lasthandoff: 03/13/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Propriedades e métodos sobrecarregados (Visual Basic)
Sobrecarga é a criação de mais de um procedimento, construtor de instância ou propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.  
  
## <a name="overloading-usage"></a>Sobrecarga de uso  
 Sobrecarga é especialmente útil quando o modelo de objeto determina que utilizam nomes idênticos para procedimentos que operam em diferentes tipos de dados. Por exemplo, uma classe que pode exibir vários tipos diferentes de dados poderia ter `Display` procedimentos que esta aparência:  
  
 [!code-vb[VbVbalrOOP&#64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:  
  
 [!code-vb[VbVbalrOOP&#65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 Sobrecarga torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado. Por exemplo, sobrecarregados `Display` método discutido anteriormente pode ser chamado com qualquer uma das seguintes linhas de código:  
  
 [!code-vb[VbVbalrOOP&#66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 Em tempo de execução [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o procedimento correto com base nos tipos de dados dos parâmetros você especifica.  
  
## <a name="overloading-rules"></a>Sobrecarga de regras  
 Você pode criar um membro sobrecarregadas para uma classe adicionando dois ou mais propriedades ou métodos com o mesmo nome. Exceto para membros derivados sobrecarregados, cada membro sobrecarregadas deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferencial ao sobrecarregar uma propriedade ou um procedimento:  
  
-   Modificadores, como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.  
  
-   Nomes de parâmetros  
  
-   Tipos de procedimentos de retorno  
  
 O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar essa palavra-chave.  
  
 Classes derivadas podem sobrecarregar membros herdados que possuem membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*. Se o `Overloads` palavra-chave é usada quando o sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias da classe derivada.  
  
 Se o `Overloads` palavra-chave for omitida quando um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro de sobrecarga e a sobrecarga é chamada *sombreamento por nome*. Sombreamento pelo nome substitui a implementação herdada de um membro, e torna todas as outras sobrecargas indisponível para instâncias da classe derivada e suas decedents.  
  
 O `Overloads` e `Shadows` modificadores não podem ser usados com a mesma propriedade ou método.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir cria os métodos sobrecarregados que aceitam um uma `String` ou `Decimal` representação de um valor em dólares e retornar uma cadeia de caracteres que contém o imposto sobre vendas.  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Para usar esse exemplo para criar um método sobrecarregado  
  
1.  Abra um novo projeto e adicionar uma classe denominada `TaxClass`.  
  
2.  Adicione o seguinte código para o `TaxClass` classe.  
  
     [!code-vb[VbVbalrOOP&#67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  Adicione o seguinte procedimento para seu formulário.  
  
     [!code-vb[VbVbalrOOP&#68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  Adicionar um botão para o formulário e chamar o `ShowTax` procedimento o `Button1_Click` evento do botão.  
  
5.  Execute o projeto e clique no botão no formulário para testar a sobrecarga `ShowTax` procedimento.  
  
 Em tempo de execução, o compilador escolhe a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados. Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres. Imposto é $5,12" é exibida. `TaxAmount`é chamado com um `Decimal` valor na segunda vez e a mensagem, "preço é um Decimal. Imposto é $5,12" é exibida.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Noções básicas sobre herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
