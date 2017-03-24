---
title: "Visão geral de constantes (Visual Basic) | Documentos do Microsoft"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.openlocfilehash: 8004045d233da0db017b26b350743ad9f8d61845
ms.lasthandoff: 03/13/2017

---
# <a name="constants-overview-visual-basic"></a>Visão geral de constantes (Visual Basic)
Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados. Constantes armazenam valores que, como o nome já diz, permanecem os mesmos durante a execução de um aplicativo. Você pode significativamente melhorar a legibilidade do código e facilitar a manutenção usando constantes. Usá-los no código que contém valores que reaparecem ou dependem de certos números que são difíceis de lembrar ou não tem significado óbvio.  
  
## <a name="how-to-create-and-use-constants"></a>Como criar e usar constantes  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]contém um número de constantes pré-definidas, usadas principalmente para impressão e exibição. Você também pode criar suas próprias constantes com a `Const` declaração, usando as mesmas diretrizes que você faria para criar um nome de variável. Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.  
  
 Escopo de uma constante, que é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome, é o mesmo que uma variável declarada no mesmo local. Para criar uma constante que existe dentro do escopo de um determinado procedimento, declare-a dentro do procedimento. Para criar uma constante que está disponível em toda o aplicativo, declare-a usando o `Public` palavra-chave na seção de declarações da classe.  
  
> [!NOTE]
>  Embora constantes de alguma maneira se assemelharem a variáveis, você não pode modificá-las ou atribuir novos valores para eles em variáveis.  
  
 As constantes que você usa em seu código podem ser definidas pelo modelo de objeto para controles ou componentes que você trabalha com, ou podem ser definidos pelo usuário (ou seja, aqueles você mesmo cria).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes de tempo de compilação e tempo de execução  
 Uma constante de tempo de compilação é computada no momento em que o código é compilado, enquanto uma constante de tempo de execução pode ser calculada apenas enquanto o aplicativo é executado. Uma constante de tempo de compilação terá o mesmo valor cada vez que um aplicativo é executado, enquanto uma constante de tempo de execução pode mudar cada vez. Constantes de tempo de compilação são necessárias em casos como limites de matriz, expressões case ou inicializadores.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Definição|Termo|  
|---|---|  
|[Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explica como usar o `Const` instrução para declarar uma constante e definir seu valor; ao declarar uma constante, você atribuir um nome significativo para o valor.|  
|[Constantes Definidas pelo Usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Descreve como criar suas próprias constantes, incluindo informações sobre o escopo e como evitar referências circulares.|  
|[Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fornece informações sobre como o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador inicializa constantes quando `Option Explicit` está desativado.|  
|[Como agrupar valores constantes relacionados](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Demonstra como agrupar valores constantes que estão relacionados.|  
  
## <a name="reference"></a>Referência  
  
|Definição|Termo|  
|---|---|  
|[Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Lista as constantes predefinidas pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].|  
|[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Descreve o `Const` instrução e seu uso.|  
|[Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Descreve o `Option Strict` instrução e seu uso.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Como: inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
