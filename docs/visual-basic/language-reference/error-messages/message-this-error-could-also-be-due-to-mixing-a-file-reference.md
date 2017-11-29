---
title: "&lt;mensagem&gt; esse erro também pode ocorrer devido à combinação de uma referência de arquivo com uma referência ao assembly &#39;&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;mensagem&gt; esse erro também pode ocorrer devido à combinação de uma referência de arquivo com uma referência ao assembly &#39;&lt; AssemblyName&gt;&#39;
\<mensagem > Esse erro também pode ocorrer devido à combinação de uma referência de arquivo com uma referência ao assembly '\<assemblyname >. Nesse caso, tente substituir a referência de arquivo para '\<assemblyfilename >' no projeto '\<projectname1 >' com uma referência de projeto para '\<projectname2 >'.  
  
 Código em seu projeto acessa um membro de outro projeto, mas a configuração de sua solução não permite que o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador para resolver a referência.  
  
 Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador deve ter uma referência a esse assembly. Isso deve ser uma referência única, não ambígua que não cause referências circulares entre projetos.  
  
 **ID do erro:** BC30971  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso de arquivo e a frequência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência ao projeto que contém o assembly que define o tipo que você está usando.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)  
 [Solução de Problemas de Referências Quebradas](/visualstudio/ide/troubleshooting-broken-references)
