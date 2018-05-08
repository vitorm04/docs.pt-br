---
title: Propriedades e métodos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: c0aa7c4a13e049045743044a98020a1aab2cf1a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Propriedades e métodos (Visual Basic)

Sobrecarga é a criação de mais de um procedimento, construtor de instância ou propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.  
  
## <a name="overloading-usage"></a>Sobrecarga de uso

 Sobrecarga é especialmente útil quando o modelo de objeto dita utilizar nomes idênticos de procedimentos que operam em diferentes tipos de dados. Por exemplo, uma classe que pode exibir vários tipos de dados diferentes pode ter `Display` procedimentos ter esta aparência:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Sem sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Sobrecarga torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado. Por exemplo, o sobrecarregado `Display` método discutido anteriormente pode ser chamado com qualquer uma das linhas de código a seguir:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 Em tempo de execução, o Visual Basic chama o procedimento correto com base nos tipos de dados dos parâmetros que você especificar.  
  
## <a name="overloading-rules"></a>Sobrecarga de regras

 Você pode criar um membro sobrecarregado para uma classe adicionando dois ou mais propriedades ou métodos com o mesmo nome. Exceto para membros derivados sobrecarregados, cada membro sobrecarregado deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferencial ao sobrecarregar uma propriedade ou procedimento:  
  
-   Modificadores, tais como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.  
  
-   Nomes de parâmetros  
  
-   Tipos de retorno de procedimentos  
  
 O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar a palavra-chave.  
  
 Classes derivadas podem sobrecarregar membros herdados com membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*. Se o `Overloads` palavra-chave é usada quando sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação da classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias das classe derivada.  
  
 Se o `Overloads` palavra-chave for omitida ao sobrecarregar um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro e, em seguida, a sobrecarga é chamado *sombreamento por nome*. Sombreamento pelo nome substitui a implementação herdada de um membro e torna todas as outras sobrecargas disponíveis para instâncias de classe derivada e seus decedents.  
  
 O `Overloads` e `Shadows` modificadores não podem ser usados com o mesmo método ou propriedade.  
  
### <a name="example"></a>Exemplo

 O exemplo a seguir cria os métodos sobrecarregados que aceitam um um `String` ou `Decimal` representação de um valor monetário e retornar uma cadeia de caracteres que contém o imposto sobre vendas.  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Para usar este exemplo para criar um método sobrecarregado
  
1.  Abra um novo projeto e adicione uma classe denominada `TaxClass`.  
  
2.  Adicione o seguinte código para o `TaxClass` classe.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Adicione o seguinte procedimento para seu formulário.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Adicionar um botão ao seu formulário e a chamada a `ShowTax` procedimento o `Button1_Click` eventos do botão.  
  
5.  Execute o projeto e clique no botão no formulário para testar o sobrecarregado `ShowTax` procedimento.  
  
 Em tempo de execução, o compilador escolha a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados. Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro que é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres. Imposto é $5,12" é exibida. `TaxAmount` é chamado com um `Decimal` valor na segunda vez e a mensagem, "o preço é um número Decimal. Imposto é $5,12" é exibida.  
  
## <a name="see-also"></a>Consulte também

 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
