---
title: Propriedades e métodos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677390"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Propriedades e métodos (Visual Basic)

Sobrecarga é a criação de mais de um procedimento, o construtor de instância ou a propriedade em uma classe com o mesmo nome mas com tipos diferentes de argumentos.

## <a name="overloading-usage"></a>Sobrecarga de uso

Sobrecarga é especialmente útil quando seu modelo de objeto dita utilizar nomes idênticos para os procedimentos que operam em tipos de dados diferentes. Por exemplo, uma classe que pode exibir vários tipos diferentes de dados poderia ter `Display` procedimentos ter esta aparência:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Sem a sobrecarga, você precisaria criar nomes distintos para cada procedimento, mesmo que eles fazem a mesma coisa, como mostrado a seguir:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Sobrecarregando torna mais fácil de usar propriedades ou métodos porque ele fornece uma variedade de tipos de dados que pode ser usado. Por exemplo, sobrecarregado `Display` método discutido anteriormente pode ser chamado com qualquer uma das seguintes linhas de código:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

Em tempo de execução, o Visual Basic chama o procedimento correto com base nos tipos de dados dos parâmetros que você especificar.

## <a name="overloading-rules"></a>Sobrecarga de regras

 Você pode criar um membro sobrecarregado para uma classe com a adição de dois ou mais propriedades ou métodos com o mesmo nome. Exceto para membros derivados sobrecarregados, cada membro sobrecarregado deve ter listas de parâmetros diferentes e os itens a seguir não podem ser usados como um recurso diferenciador ao sobrecarregar uma propriedade ou procedimento:

- Modificadores, tais como `ByVal` ou `ByRef`, que se aplicam a um membro ou parâmetros do membro.

- Nomes de parâmetros

- Tipos de retorno de procedimentos

O `Overloads` palavra-chave é opcional quando a sobrecarga, mas se houver sobrecarregado membro usa o `Overloads` palavra-chave e, em seguida, todos os outros membros sobrecarregados com o mesmo nome também devem especificar essa palavra-chave.

As classes derivadas podem sobrecarregar membros herdados com membros que têm parâmetros idênticos e tipos de parâmetro, um processo conhecido como *sombreamento por nome e assinatura*. Se o `Overloads` palavra-chave é usada quando o sombreamento por nome e assinatura, a implementação da classe derivada do membro será usada em vez da implementação na classe base e todas as outras sobrecargas para esse membro estarão disponíveis para instâncias das classe derivada.

Se o `Overloads` palavra-chave for omitida, ao sobrecarregar um membro herdado com um membro que tem parâmetros idênticos e tipos de parâmetro e, em seguida, a sobrecarga é chamado *sombreamento por nome*. Sombreamento por nome substitui a implementação herdada de um membro e, em seguida, faz todas as outras sobrecargas indisponível para instâncias da classe derivada e seus decedents.

O `Overloads` e `Shadows` modificadores não podem ambos ser usados com a mesma propriedade ou método.

### <a name="example"></a>Exemplo

O exemplo a seguir cria métodos sobrecarregados que aceitam a um `String` ou `Decimal` representação de um valor monetário e o retorno de uma cadeia de caracteres que contém o imposto sobre vendas.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Para usar este exemplo para criar um método sobrecarregado

1. Abra um novo projeto e adicione uma classe chamada `TaxClass`.

2. Adicione o código a seguir à classe `TaxClass`.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Adicione o procedimento a seguir ao seu formulário.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Adicionar um botão ao formulário e chame o `ShowTax` procedimento do `Button1_Click` evento do botão.

5. Execute o projeto e clique no botão no formulário para testar sobrecarregado `ShowTax` procedimento.

Em tempo de execução, o compilador escolhe a função sobrecarregada apropriada que corresponde aos parâmetros que está sendo usados. Quando você clica no botão, o método sobrecarregado é chamado pela primeira vez com um `Price` parâmetro que é uma cadeia de caracteres e a mensagem "o preço é uma cadeia de caracteres. Imposto é $5,12" é exibida. `TaxAmount` é chamado com um `Decimal` valor na segunda vez e a mensagem, "preço é um Decimal. Imposto é $5,12" é exibida.

## <a name="see-also"></a>Consulte também

- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Noções Básicas de Herança](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
