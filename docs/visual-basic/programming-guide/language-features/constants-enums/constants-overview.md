---
title: Visão geral de constantes (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2ec43254013df5444048b5197489c55217d5328a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="constants-overview-visual-basic"></a>Visão geral de constantes (Visual Basic)
Uma constante é um nome significativo que toma o lugar de um número ou uma cadeia de caracteres que não é alterado. Constantes armazenam valores que, como o nome implica, permanecem os mesmos durante a execução de um aplicativo. Muito pode melhorar a legibilidade do código e facilitar a manutenção usando constantes. Usá-los no código que contém valores que reaparecem ou dependem de certos números que são difíceis de lembrar ou não tem significado óbvio.  
  
## <a name="how-to-create-and-use-constants"></a>Como criar e usar constantes  
 Visual Basic contém um número de constantes predefinidas, usando principalmente para impressão e exibição. Você também pode criar suas próprias constantes com o `Const` instrução, usando as mesmas diretrizes que você faria para criar um nome de variável. Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.  
  
 Escopo de uma constante, que é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome, é o mesmo de uma variável declarada no mesmo local. Para criar uma constante que existe dentro do escopo de um determinado procedimento, declare-o dentro do procedimento. Para criar uma constante que está disponível em um aplicativo, declare-o usando o `Public` palavra-chave na seção de declarações da classe.  
  
> [!NOTE]
>  Embora as constantes um pouco semelhante a variáveis, não é possível modificá-las ou atribuir novos valores para eles em variáveis.  
  
 As constantes que você usa em seu código podem ser definidas pelo modelo de objeto para controles ou componentes que funcionam com ou eles podem ser definidas pelo usuário (ou seja, aquelas criadas por você).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes de tempo de compilação e tempo de execução  
 Uma constante de tempo de compilação é computada no momento em que o código é compilado, enquanto uma constante de tempo de execução pode ser calculada apenas enquanto o aplicativo está em execução. Uma constante de tempo de compilação terá o mesmo valor de cada vez que um aplicativo é executado, enquanto uma constante de tempo de execução pode mudar cada vez. Constantes de tempo de compilação são necessárias em casos como limites de matriz, expressões case ou inicializadores.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Definição|Termo|  
|---|---|  
|[Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explica como usar o `Const` instrução para declarar uma constante e definir seu valor; declarando uma constante, você atribuir um nome significativo para o valor.|  
|[Constantes Definidas pelo Usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Descreve como criar suas próprias constantes, incluindo informações sobre o escopo e como evitar referências circulares.|  
|[Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fornece informações sobre como o compilador do Visual Basic inicializa constantes quando `Option Explicit` está desativado.|  
|[Como agrupar valores constantes relacionados](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Demonstra como agrupar valores constantes que estão relacionados.|  
  
## <a name="reference"></a>Referência  
  
|Definição|Termo|  
|---|---|  
|[Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Lista as constantes predefinidas pelo Visual Basic.|  
|[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Descreve o `Const` instrução e seu uso.|  
|[Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Descreve o `Option Strict` instrução e seu uso.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
