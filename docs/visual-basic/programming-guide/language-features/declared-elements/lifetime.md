---
title: Tempo de vida no Visual Basic | Documentos do Microsoft
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
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
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
ms.openlocfilehash: fa0cbdf4a8fe5e8fc41e4e4f373c79451fb7b75f
ms.lasthandoff: 03/13/2017

---
# <a name="lifetime-in-visual-basic"></a>Tempo de vida no Visual Basic
O *tempo de vida* de um elemento declarado é o período de tempo durante o qual ele está disponível para uso. Variáveis são os únicos elementos que têm tempo de vida. Para essa finalidade, o compilador trata parâmetros de procedimento e função retorna como casos especiais de variáveis. O tempo de vida de uma variável representa o período de tempo durante o qual ele pode conter um valor. Seu valor pode ser alterado durante seu ciclo de vida, mas ele sempre contém um valor.  
  
## <a name="different-lifetimes"></a>Tempos de vida diferentes  
 A *variável membro* (declarado no nível de módulo, fora de qualquer procedimento) geralmente tem a mesma duração do elemento no qual ela é declarada. Existe uma variável não compartilhada declarada em uma classe ou estrutura como uma cópia separada para cada instância da classe ou estrutura na qual ela é declarada. Cada variável como tem a mesma duração sua instância. No entanto, um `Shared` variável tem apenas um único ciclo de vida, que dura durante todo o tempo de execução do seu aplicativo.  
  
 A *variável local* (declaradas dentro de um procedimento) existe somente enquanto o procedimento no qual ela é declarada é executado. Isso se aplica também aos parâmetros do procedimento e para qualquer função de retornada. No entanto, se esse procedimento chama outros procedimentos, as variáveis locais retêm seus valores durante a execução de procedimentos chamados.  
  
## <a name="beginning-of-lifetime"></a>Início do tempo de vida  
 Tempo de vida de uma variável local começa quando o controle entra o procedimento no qual ela é declarada. Cada variável local é inicializada com o valor padrão para seu tipo de dados assim que o procedimento começa em execução. Quando o procedimento encontra um `Dim` instrução que especifica os valores iniciais, ele define essas variáveis para esses valores, mesmo se seu código tinha já outros valores atribuídos a eles.  
  
 Cada membro de uma variável de estrutura é inicializado como se fosse uma variável separada. Da mesma forma, cada elemento de uma variável de matriz é inicializado individualmente.  
  
 Variáveis declaradas dentro de um bloco dentro de um procedimento (como um `For` loop) são inicializados na entrada para o procedimento. Essas inicializações entram em vigor se seu código nunca executa o bloco ou não.  
  
## <a name="end-of-lifetime"></a>Fim da vida útil  
 Quando um procedimento termina, os valores das suas variáveis locais não são preservados, e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] recupera sua memória. Na próxima vez que você chamar o procedimento, todas as suas variáveis locais são criadas novamente e reinicializadas.  
  
 Quando termina de uma instância de uma classe ou estrutura, suas variáveis não compartilhadas perder sua memória e seus valores. Cada nova instância da classe ou estrutura cria e reinicializa suas variáveis não compartilhadas. No entanto, `Shared` variáveis são preservadas até que seu aplicativo é interrompido.  
  
## <a name="extension-of-lifetime"></a>Extensão do tempo de vida  
 Se você declarar uma variável local com o `Static` palavra-chave, seu tempo de vida é maior do que o tempo de execução de seu procedimento. A tabela a seguir mostra como a declaração do procedimento determina quanto tempo um `Static` variável existe.  
  
|Local do procedimento e compartilhamento|Começa a vida útil da variável estática|Fim da vida útil da variável estática|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Em um módulo (compartilhado por padrão)|Na primeira vez que o procedimento é chamado.|Quando seu aplicativo é interrompido|  
|Em uma classe, `Shared` (procedimento não é um membro de instância)|Na primeira vez que o procedimento é chamado em uma instância específica ou no nome de classe ou estrutura em si|Quando seu aplicativo é interrompido|  
|Em uma instância de uma classe, não `Shared` (procedimento é um membro de instância)|Na primeira vez que o procedimento é chamado na instância específica|Quando a instância é liberada para coleta de lixo (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Variáveis estáticas de mesmo nome  
 Você pode declarar variáveis estáticas com o mesmo nome em mais de um procedimento. Se você fizer isso, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador considera cada variável como um elemento separado. A inicialização de um dessas variáveis não afeta os valores das outras. O mesmo se aplica se você define um procedimento com um conjunto de sobrecargas e declarar uma variável estática com o mesmo nome em cada sobrecarga.  
  
## <a name="containing-elements-for-static-variables"></a>Elementos continentes para variáveis estáticas  
 Você pode declarar uma variável local estática em uma classe, isto é, dentro de um procedimento na classe. No entanto, você não pode declarar uma variável local estática em uma estrutura, como um membro de estrutura ou uma variável local de um procedimento dentro dessa estrutura.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir declara uma variável com o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave. (Observe que não é necessário o `Dim` palavra-chave quando a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) usa um modificador, como `Static`.)  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrKeywords&13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>Comentários  
 No exemplo anterior, a variável `applesSold` continua existindo depois do procedimento `runningTotal` retorna para o código de chamada. Na próxima vez que `runningTotal` é chamado, `applesSold` manterá seu valor calculado anteriormente.  
  
 Se `applesSold` tivesse sido declarada sem usar `Static`, os valores acumulados anteriormente não poderiam ser preservados entre chamadas para `runningTotal`. Na próxima vez que `runningTotal` foi chamado, `applesSold` seria ter sido recriada e inicializada como 0, e `runningTotal` teria simplesmente retornado o mesmo valor com o qual ele foi chamado.  
  
### <a name="compiling-the-code"></a>Compilando o código  
 Você pode inicializar o valor de uma variável local estática como parte de sua declaração. Se você declarar uma matriz para ser `Static`, você pode inicializar sua ordem (número de dimensões), o tamanho de cada dimensão e os valores dos elementos individuais.  
  
### <a name="security"></a>Segurança  
 No exemplo anterior, você pode produzir o mesmo tempo de vida, declarando `applesSold` no nível de módulo. Se você tiver alterado o escopo de uma variável dessa maneira, no entanto, o procedimento não teria acesso exclusivo a ele. Como outros procedimentos poderiam acessar `applesSold` e alterar seu valor, o total de execução pode não ser confiável e o código poderia ser mais difícil de manter.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [Nada](../../../../visual-basic/language-reference/nothing.md)   
 [Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)
