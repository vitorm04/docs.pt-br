---
title: Visão geral de constantes (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 34f3dee4edba58375c5c84b579e39a8a29ebc1bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737683"
---
# <a name="constants-overview-visual-basic"></a>Visão geral de constantes (Visual Basic)
Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados. Constantes armazenam valores que, como o nome implica, permanecem os mesmos durante a execução de um aplicativo. Você pode significativamente melhorar a legibilidade do código e facilitam a manutenção usando constantes. Usá-los no código que contém valores que reaparecem ou dependem de certos números que são difíceis de lembrar ou não tem significado óbvio.  
  
## <a name="how-to-create-and-use-constants"></a>Como criar e usar constantes  
 Visual Basic contém um número de constantes predefinidas, principalmente usando para impressão e exibição. Você também pode criar suas próprias constantes com a `Const` instrução, usando as mesmas diretrizes que você faria para a criação de um nome de variável. Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.  
  
 Escopo de uma constante, que é o conjunto de todos os códigos que podem fazer referência a ele sem qualificar seu nome, é o mesmo que de uma variável declarada no mesmo local. Para criar uma constante que existe dentro do escopo de um determinado procedimento, declare-o dentro do procedimento. Para criar uma constante que esteja disponível por meio de um aplicativo, declare-o usando o `Public` palavra-chave na seção de declarações da classe.  
  
> [!NOTE]
>  Embora as constantes se parecer um pouco com variáveis, não é possível modificá-las ou atribuir novos valores a eles como faria para variáveis.  
  
 As constantes que você pode usar em seu código podem ser definidas pelo modelo de objeto para controles ou componentes que funcionam com, ou podem ser definidas pelo usuário (ou seja, aqueles você mesmo cria).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes de tempo de compilação e tempo de execução  
 Uma constante de tempo de compilação é calculada no momento em que o código é compilado, enquanto uma constante de tempo de execução pode ser calculada apenas enquanto o aplicativo está em execução. Uma constante de tempo de compilação terá o mesmo valor sempre que um aplicativo é executado, enquanto uma constante de tempo de execução pode mudar cada vez. Constantes de tempo de compilação são necessárias para casos como limites de matriz, expressões case ou inicializadores.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Definição|Termo|  
|---|---|  
|[Como: Declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explica como usar o `Const` instrução para declarar uma constante e definir seu valor; ao declarar uma constante, você deve atribuir um nome significativo para o valor.|  
|[Constantes Definidas pelo Usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Descreve como criar suas próprias constantes, incluindo informações sobre o escopo e como evitar referências circulares.|  
|[Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fornece informações sobre como o compilador do Visual Basic inicializa constantes quando `Option Explicit` está desativado.|  
|[Como: Agrupar valores constantes relacionados](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Demonstra como agrupar valores constantes relacionados.|  
  
## <a name="reference"></a>Referência  
  
|Definição|Termo|  
|---|---|  
|[Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Lista as constantes predefinidas pelo Visual Basic.|  
|[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Descreve o `Const` instrução e seu uso.|  
|[Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Descreve o `Option Strict` instrução e seu uso.|  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Como: Inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
