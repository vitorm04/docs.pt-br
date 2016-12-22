---
title: "Compila&#231;&#227;o condicional no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "compilação, condicional"
  - "compilação condicional, sobre a compilação condicional"
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Compila&#231;&#227;o condicional no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em  *compilação condicional*, determinados blocos de código em um programa são compilados seletivamente, enquanto outros são ignorados.  
  
 Por exemplo, você pode querer escrever declarações de depuração que comparam a velociade de diferentes abordagens para a mesma tarefa de programação, ou pode querer alocar um aplicativo para múltiplas linguagens.  Declaração de compilação condicional são designadas para executar durante o tempo de compilação, e não em tempo de execução.  
  
 Denotar o blocos de código seja compilado condicionalmente com o `#If...Then...#Else` diretiva.  Por exemplo, para criar versões em Francês e Alemão do mesmo aplicativo a partir do mesmo código fonte, você deve incorporar segmentos de código da plataforma específica em declarações  `#If...Then` usando as constantes `FrenchVersion` e `GermanVersion` pré\-definidas.  O exemplo a seguir demonstra como:  
  
 [!CODE [VbVbalrConditionalComp#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#5)]  
  
 Se você definir o valor de `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão em francês é compilado.  Se você configurar o valor da constante `GermanVersion` para `True`, o compilador usará a versão em Alemão.  Se nenhuma for configurada para `True`, será executado o código no último bloco `Else`.  
  
> [!NOTE]
>  Autocompletar não funcionará quando se estiver editando o código e utilizando diretivas de compilação condicional e o código não for parte da ramificação atual.  
  
## Declarar constantes de compilação condicional  
 Você pode definir constantes de compilação condicional em uma das três maneiras:  
  
-   No  **Project Designer**  
  
-   Na linha de comando ao usar o compilador de linha de comando  
  
-   No seu código.  
  
 Constantes de compilação condicional têm um escopo especial e não podem ser acessados a partir de código padrão.  O escopo de uma constante de compilação condicional depende da maneira que ele está definido.  A tabela a seguir lista o escopo de constantes declaradas usando cada uma das três maneiras mencionadas acima.  
  
|||  
|-|-|  
|Como é definida de constante|Escopo da constante|  
|**Designer de projeto**|Público para todos os arquivos do projeto.|  
|Linha de comando|Públicos para todos os arquivos são passados para o compilador de linha de comando|  
|`#Const`instrução em código|Particular para o arquivo no qual é declarada|  
  
||  
|-|  
|Para definir constantes no Project Designer|  
|-   Antes de criar o seu arquivo executável, definir constantes no  **Project Designer** , seguindo as etapas fornecidas em [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).|  
  
||  
|-|  
|Para definir constantes na linha de comando|  
|-   Use o **\/d** switch entre constantes de compilação condicional, como no exemplo a seguir:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Nenhum espaço é necessário entre a **\/d** switch e a primeira constante.  Para obter mais informações, consulte [\/define](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Declarações de linha de comando substituem declarações inseridas na  **Project Designer**, mas não as apague.  Argumentos definidos no  **Project Designer** permanecerão em vigor para compilações subseqüentes.<br />     Ao escrever constantes no próprio código, existem regras rígidas quanto à sua colocação, desde que o escopo seja todo o módulo em que elas são declaradas.|  
  
||  
|-|  
|Para definir constantes em seu código.|  
|-   Coloque as constantes no bloco de declaração do módulo no qual eles são usados.  Isso ajuda a manter seu código organizado e fácil de ler.|  
  
## Tópicos relacionados  
  
|||  
|-|-|  
|Título|Descrição|  
|[Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Oferece sugestões para tornar seu código fácil de ler e manter.|  
  
## Referência  
 [Diretiva \#Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)