---
title: Referência obrigatória ao assembly &#39; &lt;assemblyidentity&gt; &#39; que contém o tipo &#39; &lt;typename&gt;&#39;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre projetos &#39; &lt;projectname1&gt; &#39; e &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 1a0c2a2fd235026729901153a0c0c300f914a78f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553003"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Referência obrigatória ao assembly &#39; &lt;assemblyidentity&gt; &#39; que contém o tipo &#39; &lt;typename&gt;&#39;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre projetos &#39; &lt;projectname1&gt; &#39; e &#39; &lt;projectname2&gt;&#39;
Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora de seu projeto. No entanto, você tem referências do projeto para definir o tipo de mais de um assembly.  
  
 Os projetos citados produzem assemblies com o mesmo nome. Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.  
  
 Para acessar um tipo definido em outro assembly, o compilador do Visual Basic deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não faz com que referências circulares entre projetos.  
  
 **ID do erro:** BC30969  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso de arquivo e a frequência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.  
  
## <a name="see-also"></a>Consulte também
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
- [Solução de Problemas de Referências Quebradas](/visualstudio/ide/troubleshooting-broken-references)
