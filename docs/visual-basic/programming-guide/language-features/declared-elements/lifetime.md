---
title: Tempo de vida no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 15fb6895836de95d37081c44973f455622da178e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976038"
---
# <a name="lifetime-in-visual-basic"></a>Tempo de vida no Visual Basic
O *tempo de vida* de um elemento declarado é o período de tempo durante o qual ele está disponível para uso. As variáveis são os únicos elementos que têm o tempo de vida. Para essa finalidade, o compilador trata os parâmetros de procedimento e função retorna como casos especiais de variáveis. O tempo de vida de uma variável representa o período de tempo durante o qual ele pode conter um valor. Seu valor pode mudar durante sua vida útil, mas ele sempre contém algum valor.  
  
## <a name="different-lifetimes"></a>Tempos de vida diferentes  
 Um *variável de membro* (declarado no nível de módulo, fora de qualquer procedimento) normalmente tem a mesma duração como o elemento no qual ela é declarada. Uma variável não compartilhada declarada em uma classe ou estrutura existe como uma cópia separada para cada instância da classe ou estrutura na qual ela é declarada. Cada variável como tem a mesma duração de sua instância. No entanto, um `Shared` variável tem apenas um único tempo de vida, que dura o tempo todo, seu aplicativo está em execução.  
  
 Um *variável local* (declarada dentro de um procedimento) existe somente enquanto o procedimento no qual ela é declarada é executado. Isso se aplica também aos parâmetros do procedimento e para qualquer função de retornada. No entanto, se esse procedimento chama outros procedimentos, as variáveis locais retêm seus valores durante a execução de procedimentos chamados.  
  
## <a name="beginning-of-lifetime"></a>Início do tempo de vida  
 Tempo de vida da variável local é iniciada quando o controle entra o procedimento no qual ela é declarada. Cada variável local é inicializada com o valor padrão para seu tipo de dados assim que o procedimento começa em execução. Quando o procedimento encontra um `Dim` declaração que especifica os valores iniciais, ele define essas variáveis para esses valores, mesmo se seu código tinha já outros valores atribuídos a eles.  
  
 Cada membro de uma variável de estrutura é inicializado como se fosse uma variável separada. Da mesma forma, cada elemento de uma variável de matriz é inicializado individualmente.  
  
 As variáveis declaradas dentro de um bloco dentro de um procedimento (como um `For` loop) são inicializados na entrada para o procedimento. Essas inicializações entram em vigor, se seu código nunca executa o bloco.  
  
## <a name="end-of-lifetime"></a>Fim do tempo de vida  
 Quando um procedimento é encerrado, os valores de suas variáveis locais não são preservados e Visual Basic recupera sua memória. Na próxima vez que você chamar o procedimento, todas as suas variáveis locais são criadas novamente e reinicializadas.  
  
 Quando uma instância de uma classe ou estrutura é encerrada, sua variáveis não perder sua memória e seus valores. Cada nova instância da classe ou estrutura cria e reinicializa suas variáveis não compartilhadas. No entanto, `Shared` variáveis são preservadas até que seu aplicativo é interrompido.  
  
## <a name="extension-of-lifetime"></a>Extensão de tempo de vida  
 Se você declarar uma variável local com o `Static` palavra-chave, o seu tempo de vida é maior que o tempo de execução de seu procedimento. A tabela a seguir mostra como a declaração de procedimento determina quanto tempo um `Static` variável existe.  
  
|Compartilhamento e o local do procedimento|Começa a vida útil da variável estática|Vida útil da variável estática extremidades|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Em um módulo (compartilhado por padrão)|Na primeira vez em que o procedimento é chamado|Quando seu aplicativo é interrompido|  
|Em uma classe, `Shared` (procedimento não é um membro de instância)|Na primeira vez que o procedimento é chamado em uma instância específica ou sobre o nome de classe ou estrutura em si|Quando seu aplicativo é interrompido|  
|Em uma instância de uma classe, não `Shared` (procedimento é um membro de instância)|Na primeira vez em que o procedimento é chamado na instância específica|Quando a instância é liberada para coleta de lixo (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Variáveis estáticas de mesmo nome  
 Você pode declarar variáveis estáticas com o mesmo nome em mais de um procedimento. Se você fizer isso, o compilador do Visual Basic considera cada variável como um elemento separado. A inicialização de uma dessas variáveis não afeta os valores dos outros. O mesmo se aplica se você define um procedimento com um conjunto de sobrecargas e declarar uma variável estática com o mesmo nome em cada sobrecarga.  
  
## <a name="containing-elements-for-static-variables"></a>Que contém elementos para variáveis estáticas  
 Você pode declarar uma variável local estática em uma classe, ou seja, dentro de um procedimento nessa classe. No entanto, você não pode declarar uma variável local estática em uma estrutura, como um membro da estrutura ou como uma variável local de um procedimento dentro dessa estrutura.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir declara uma variável com o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave. (Observe que não é necessário o `Dim` palavra-chave quando o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) usa um modificador como `Static`.)  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Comentários  
 No exemplo anterior, a variável `applesSold` continua existindo depois do procedimento `runningTotal` retorna para o código de chamada. Na próxima vez que `runningTotal` é chamado, `applesSold` retém seu valor calculado anteriormente.  
  
 Se `applesSold` tivesse sido declarada sem usar `Static`, os valores acumulados anteriormente não poderiam ser preservados entre chamadas para `runningTotal`. Na próxima vez que `runningTotal` foi chamado, `applesSold` teria sido recriado e inicializado como 0, e `runningTotal` poderia simplesmente ter retornado o mesmo valor com o qual ele foi chamado.  
  
### <a name="compiling-the-code"></a>Compilando o código  
 Você pode inicializar o valor de uma variável local estática como parte de sua declaração. Se você declarar uma matriz a ser `Static`, você pode inicializar sua classificação (número de dimensões), o tamanho de cada dimensão e os valores dos elementos individuais.  
  
### <a name="security"></a>Segurança  
 No exemplo anterior, você pode produzir o mesmo tempo de vida, declarando `applesSold` no nível de módulo. Se você tiver alterado o escopo de uma variável dessa forma, no entanto, o procedimento não teria acesso exclusivo a ele. Como outros procedimentos poderiam acessar `applesSold` e altere seu valor, o total de execução pode não ser confiável e o código poderia ser mais difícil de manter.  
  
## <a name="see-also"></a>Consulte também
- [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Estático](../../../../visual-basic/language-reference/modifiers/static.md)
