---
title: Compilação condicional no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 4698435cb2ab15d16d8a8a898a01a9ffbc4f69c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639801"
---
# <a name="conditional-compilation-in-visual-basic"></a>Compilação condicional no Visual Basic
Na *compilação condicional*, blocos específicos de código em um programa são compilados seletivamente, enquanto outros são ignorados.  
  
 Por exemplo, você talvez queira escrever declarações de depuração que comparam a velocidade das diferentes abordagens para a mesma tarefa de programação, ou você talvez queira localizar um aplicativo para vários idiomas. Instruções de compilação condicional são projetadas para execução durante o tempo de compilação, não em tempo de execução.  
  
 Você denota blocos de código seja compilado condicionalmente com o `#If...Then...#Else` diretiva. Por exemplo, para criar o francês e alemão versões do mesmo aplicativo no mesmo código-fonte, você deve inserir segmentos de código específico da plataforma na `#If...Then` instruções usando as constantes predefinidas `FrenchVersion` e `GermanVersion`. O exemplo a seguir demonstra como:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Se você definir o valor da `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão em francês é compilado. Se você definir o valor de `GermanVersion` constante a ser `True`, o compilador usa a versão em alemão. Se nenhum dos dois for definido como `True`, o código no último `Else` execução do bloco.  
  
> [!NOTE]
>  Preenchimento automático será não funcionará quando a edição de código e usar diretivas de compilação condicional, se o código não faz parte do branch atual.  
  
## <a name="declaring-conditional-compilation-constants"></a>Declarando constantes de compilação condicional  
 Você pode definir as constantes de compilação condicional em uma das três maneiras:  
  
- No **Designer de projeto**  
  
- Na linha de comando ao usar o compilador de linha de comando  
  
- Em seu código  
  
 Constantes de compilação condicional têm um escopo especial e não podem ser acessados de código padrão. O escopo de uma constante de compilação condicional é dependendo da forma que ele está definido. A tabela a seguir lista o escopo das constantes declaradas usando cada uma das três maneiras mencionadas acima.  
  
|Como a constante é definida|Escopo de constante|  
|---|---|  
|**Designer de projeto**|Público para todos os arquivos no projeto|  
|Linha de comando|Público para todos os arquivos passados para o compilador de linha de comando|  
|`#Const` instrução no código|Privado para o arquivo no qual ela é declarada|  
  
|Para definir constantes no Designer de projeto|  
|---|  
|-A antes de criar seu arquivo executável, definir constantes na **Designer de projeto** seguindo as etapas fornecidas [propriedades de solução e gerenciando projetos](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Para definir constantes na linha de comando|  
|---|  
|– Use o **/d** switch para inserir as constantes de compilação condicional, como no exemplo a seguir:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Nenhum espaço é necessário entre o **/d** switch e a primeira constante. Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Declarações de linha de comando substituem as declarações inseridas na **Designer de projeto**, mas não apagados. Argumentos definidos **Designer de projeto** permanecem em vigor para as compilações subsequentes.<br />     Ao escrever constantes no próprio código, existem regras rígidas sobre seu posicionamento, como seu escopo é todo o módulo no qual eles são declarados.|  
  
|Para definir constantes em seu código|  
|---|  
|-Coloque as constantes no bloco de declaração do módulo no qual eles são usados. Isso ajuda a manter seu código organizado e fácil de ler.|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|---|---|  
|[Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Fornece sugestões para tornar mais fácil de ler e manter o seu código.|  
  
## <a name="reference"></a>Referência  
 [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
