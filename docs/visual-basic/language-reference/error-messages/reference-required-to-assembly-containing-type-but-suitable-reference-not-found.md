---
title: Referência obrigatória ao assembly '<assemblyidentity>' contendo o tipo '<typename>', mas não foi possível localizar uma referência adequada devido à ambiguidade entre os projetos '<projectname1>' e '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 2c74ed916e43bee6857df819c19ab03bef80b3c4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285188"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>Referência obrigatória ao assembly '\<assemblyidentity >' contendo o tipo '\<typename >', mas não foi possível localizar uma referência adequada devido à ambiguidade entre projetos\<projectname1 >' e '\< projectname2 >'
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
