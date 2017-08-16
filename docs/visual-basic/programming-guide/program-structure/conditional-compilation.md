---
title: "Compilação condicional no Visual Basic | Documentos do Microsoft"
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
- conditional compilation, about conditional compilation
- compilation, conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
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
ms.openlocfilehash: 4410e855b0741f15ffa631d28de0827907ab14dc
ms.lasthandoff: 03/13/2017

---
# <a name="conditional-compilation-in-visual-basic"></a>Compilação condicional no Visual Basic
Em *compilação condicional*, determinados blocos de código em um programa são compilados seletivamente, enquanto outros são ignorados.  
  
 Por exemplo, você talvez queira escrever declarações de depuração que comparam a velocidade das abordagens diferentes para a mesma tarefa de programação, ou você talvez queira localizar um aplicativo para vários idiomas. Instruções de compilação condicional são projetadas para execução durante o tempo de compilação, não em tempo de execução.  
  
 Denota blocos de código para serem condicionalmente compilados com a `#If...Then...#Else` diretiva. Por exemplo, para criar o francês e alemão versões do mesmo aplicativo no mesmo código-fonte, você deve inserir segmentos de código específico da plataforma em `#If...Then` instruções usando as constantes predefinidas `FrenchVersion` e `GermanVersion`. O exemplo a seguir demonstra como:  
  
 [!code-vb[VbVbalrConditionalComp n º&5;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 Se você definir o valor de `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão em francês é compilado. Se você definir o valor de `GermanVersion` constante para `True`, o compilador usará a versão em alemão. Se nenhuma for configurada para `True`, o código no último `Else` bloco é executado.  
  
> [!NOTE]
>  Preenchimento automático será não funcionará quando a edição de código e usando diretivas de compilação condicional, se o código não for parte da ramificação atual.  
  
## <a name="declaring-conditional-compilation-constants"></a>Declarando constantes de compilação condicional  
 Você pode definir constantes de compilação condicional em uma destas três maneiras:  
  
-   No **Designer de projeto**  
  
-   Na linha de comando ao usar o compilador de linha de comando  
  
-   Em seu código  
  
 Constantes de compilação condicional tem um escopo especial e não podem ser acessados de código padrão. O escopo de uma constante de compilação condicional é dependente da maneira que ele está definido. A tabela a seguir lista o escopo das constantes declaradas usando cada uma das três maneiras mencionadas acima.  
  
|Configuração constante|Escopo de constante|  
|---|---|  
|**Designer de projeto**|Público para todos os arquivos do projeto|  
|Linha de comando|Público para todos os arquivos são passados para o compilador de linha de comando|  
|`#Const`instrução no código|Para o arquivo no qual ela é declarada privada|  
  
|Para definir constantes no Designer de projeto|  
|---|  
|-Antes de criar o arquivo executável, definir constantes no **Project Designer** seguindo as etapas fornecidas em [PONTA How to: modificar propriedades do projeto e definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).|  
  
|Para definir constantes na linha de comando|  
|---|  
|-Use o **/d** switch entre constantes de compilação condicional, como no exemplo a seguir:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Nenhum espaço é necessário entre a **/d** switch e a primeira constante. Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).<br />     Declarações de linha de comando substituem declarações inseridas no **Project Designer**, mas não apaga-los. Argumentos definidos **Project Designer** permanecerão em vigor para compilações subsequentes.<br />     Ao escrever constantes no próprio código, existem regras rígidas quanto seu posicionamento, como seu escopo é todo o módulo no qual elas são declaradas.|  
  
|Para definir constantes em seu código|  
|---|  
|-Coloque as constantes no bloco de declaração do módulo no qual eles são usados. Isso ajuda a manter seu código mais fácil de ler e organizado.|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|---|---|  
|[Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|Fornece sugestões para tornar seu código fácil de ler e manter.|  
  
## <a name="reference"></a>Referência  
 [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
