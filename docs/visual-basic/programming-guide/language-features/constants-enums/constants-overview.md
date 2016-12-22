---
title: "Vis&#227;o geral de constantes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constantes"
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral de constantes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma constante é um nome com significado que toma o lugar de um número ou cadeia de caracteres que não muda.  Constantes armazenam valores que, como o nome diz, permanecem os mesmos durante a execução de um aplicativo.  Você pode aumentar consideravelmente a legibilidade do seu código e facilitar sua manutenção usando constantes.  Use\-as no código que contém valores que reaparecem ou dependem de certos números que são difíceis de lembrar ou não tem significado óbvio.  
  
## Como criar e usar constantes.  
 O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contém um número de constantes pré\-definidas, usadas principalmente para impressão na tela.  Você pode também criar suas próprias constantes com a declaração `Const`, usando as mesmas diretrizes que você usaaria para criar o nome de uma variável.  Se a opção `Option Strict` estiver `On`, você deve explicitar o tipo da constante.  
  
 O escopo de uma constante, que é o conjunto de todo o código que pode fazer referência a ela sem se restringir a seu nome, é o mesmo que uma variável teria se declarada no mesmo lugar.  Para criar uma constante que existe dentro do escopo de um procedimento em particular, declare\-a dentro do procedimento.  Para criar uma constante que é disponível em toda o aplicativo, declare\-a usando a palavra\-chave `Public` na seção de declarações da classe.  
  
> [!NOTE]
>  Apesar das constantes de alguma maneira se assemelharem a variáveis, você não pode modificá\-las ou atribuir novos valores a elas como você faz com variáveis.  
  
 As constantes que você usa em seu código podem ser definidas pelo modelo de objeto para controles ou componentes com os quais você trabalha, ou elas podem definidas pelo usuário \(ou seja, aquelas que você mesmo cria\).  
  
## Constantes de tempo de execução e de tempo de compilação.  
 Uma constante de tempo de compilação é calculada quando o código é compilado, enquanto uma constante de tempo de execução pode ser calculada apenas enquanto o aplicativo está rodando.  Uma constante de tempo de compilação terá o mesmo valor cada vez que o aplicativo roda, enquanto uma constante de tempo de execução pode mudar a cada execução.  Constantes de tempo de compilação são necessárias em casos como limites de matriz, expressões CASE ou inicializadores de enumeração.  
  
## Nesta seção  
  
|||  
|-|-|  
|Definição|Termo|  
|[Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explica como usar a instrução `Const` para declarar uma constante e definir seu valor; declarando uma constante, você atribuir um nome significativo para o valor.|  
|[Constantes definidas pelo usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Descreve como criar suas próprias constantes, incluindo informações sobre o escopo e como evitar referências circulares.|  
|[Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fornece informações sobre como o compilador [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inicializa constantes quando `Option Explicit` está desativado.|  
|[Como agrupar valores constantes relacionados](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Demonstra como agrupar valores constantes que estão relacionados.|  
  
## Referência  
  
|||  
|-|-|  
|Definição|Termo|  
|[Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Lista as constantes predefinidas por [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].|  
|[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Descreve a instrução `Const` e seu uso.|  
|[Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Descreve a instrução `Option Strict` e seu uso.|  
  
## Consulte também  
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)