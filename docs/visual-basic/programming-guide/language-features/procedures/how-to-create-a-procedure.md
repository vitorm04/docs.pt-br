---
title: Como criar um procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344906"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Como criar um procedimento (Visual Basic)

Você coloca um procedimento entre uma instrução de declaração inicial (`Sub` ou `Function`) e uma instrução de declaração final (`End Sub` ou `End Function`). Todo o código do procedimento está entre essas instruções.

 Um procedimento não pode conter outro procedimento, portanto, suas instruções de início e término devem estar fora de qualquer outro procedimento.

 Se você tiver um código que executa a mesma tarefa em locais diferentes, você pode gravar a tarefa uma vez como um procedimento e, em seguida, chamá-la de diferentes locais em seu código.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Para criar um procedimento que não retorna um valor

1. Fora de qualquer outro procedimento, use uma instrução `Sub`, seguida por uma instrução `End Sub`.

2. Na instrução `Sub`, siga a palavra-chave `Sub` com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.

3. Coloque as instruções de código do procedimento entre as instruções `Sub` e `End Sub`.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor

1. Fora de qualquer outro procedimento, use uma instrução `Function`, seguida por uma instrução `End Function`.

2. Na instrução `Function`, siga a palavra-chave `Function` com o nome do procedimento, a lista de parâmetros entre parênteses e, em seguida, uma cláusula `As` especificando o tipo de dados do valor de retorno.

3. Coloque as instruções de código do procedimento entre as instruções `Function` e `End Function`.

4. Use uma instrução `Return` para retornar o valor para o código de chamada.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Para conectar seu novo procedimento com os blocos de código antigos e repetitivos

1. Certifique-se de definir o novo procedimento em um local onde o código antigo tenha acesso a ele.

2. No seu bloco de código repetitivo antigo, substitua as instruções que executam a tarefa repetitiva com uma única instrução que chama o procedimento de `Sub` ou `Function`.

3. Se o procedimento for um `Function` que retorna um valor, verifique se a instrução de chamada executa uma ação com o valor retornado, como armazená-lo em uma variável ou se o valor será perdido.

## <a name="example"></a>Exemplo

 O procedimento a seguir `Function` calcula o lado mais longo, ou hipotenusa, de um triângulo à direita, dado os valores para os outros dois lados:

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>Consulte também

- [Procedimentos](index.md)
- [Subprocedimentos](sub-procedures.md)
- [Procedimentos de Função](function-procedures.md)
- [Procedimentos de Propriedade](property-procedures.md)
- [Procedimentos de Operador](operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](procedure-parameters-and-arguments.md)
- [Procedimentos Recursivos](recursive-procedures.md)
- [Sobrecarga de Procedimento](procedure-overloading.md)
- [Objetos e Classes](../objects-and-classes/index.md)
- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
