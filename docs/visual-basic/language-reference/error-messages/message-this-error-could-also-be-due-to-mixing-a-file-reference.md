---
title: '&lt;mensagem&gt; esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: d4fb2a8985a21ecea5056b83d2766e8dc468180d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528986"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;mensagem&gt; esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly &#39; &lt;assemblyname&gt;&#39;
\<mensagem > Esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly '\<assemblyname >. Nesse caso, tente substituir a referência de arquivo para '\<assemblyfilename >' no projeto '\<projectname1 >' com uma referência de projeto a '\<projectname2 >'.  
  
 O código em seu projeto acessa um membro de outro projeto, mas a configuração de sua solução não permite que o compilador do Visual Basic resolver a referência.  
  
 Para acessar um tipo definido em outro assembly, o compilador do Visual Basic deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não faz com que referências circulares entre projetos.  
  
 **ID do erro:** BC30971  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso de arquivo e a frequência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência ao projeto que contém o assembly que define o tipo que você está usando.  
  
## <a name="see-also"></a>Consulte também
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
- [Solução de Problemas de Referências Quebradas](/visualstudio/ide/troubleshooting-broken-references)
