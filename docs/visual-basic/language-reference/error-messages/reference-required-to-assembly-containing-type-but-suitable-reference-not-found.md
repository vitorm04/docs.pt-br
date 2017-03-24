---
title: "Referência necessária para o assembly &quot;&lt;assemblyidentity&gt;&quot;contendo o tipo&quot;&lt;typename&gt;&quot;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre os projetos&lt;projectname1&gt;&quot;e&quot;&lt;projectname2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
dev_langs:
- VB
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 38f016b9d0de053c9a95a6d4a4d810d55af903e9
ms.lasthandoff: 03/13/2017

---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Referência necessária para o assembly '&lt;assemblyidentity&gt;'contendo o tipo'&lt;typename&gt;', mas não foi possível encontrar uma referência adequada devido à ambiguidade entre os projetos&lt;projectname1&gt;'e'&lt;projectname2&gt;'
Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora do seu projeto. No entanto, você tem referências do projeto a mais de um assembly definindo o tipo.  
  
 Os projetos citados produzem assemblies com o mesmo nome. Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.  
  
 Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve ter uma referência a esse assembly. Isso deve ser uma referência única e não ambígua, que não cause referências circulares entre projetos.  
  
 **ID do erro:** BC30969  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência. Para essa decisão, você pode usar critérios, como a facilidade de acesso a arquivos e a frequência de atualizações.  
  
2.  Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Solução de Problemas de Referências Quebradas](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)
