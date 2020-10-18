---
title: <message> Este erro também poderia ocorrer devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly '<assemblyname>'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 9340c5c58c0cdb70c517534a339f57eb9ec1f906
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162421"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>BC30971: \<message> esse erro também pode ser devido à combinação de uma referência de arquivo com uma referência de projeto para o assembly ' \<assemblyname> '

\<message> Esse erro também pode ser devido à combinação de uma referência de arquivo com uma referência de projeto para o assembly ' \<assemblyname> . Nesse caso, tente substituir a referência de arquivo para ' \<assemblyfilename> ' no projeto ' \<projectname1> ' por uma referência de projeto para ' \<projectname2> '.

 O código em seu projeto acessa um membro de outro projeto, mas a configuração da sua solução não permite que o compilador Visual Basic resolva a referência.

 Para acessar um tipo definido em outro assembly, o compilador Visual Basic deve ter uma referência a esse assembly. Essa deve ser uma referência única e não ambígua que não cause referências circulares entre projetos.

 **ID do erro:** BC30971

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Determine qual projeto produz o melhor assembly para referência do seu projeto. Para essa decisão, você pode usar critérios como a facilidade de acesso a arquivos e a frequência de atualizações.

2. Nas propriedades do projeto, adicione uma referência ao projeto que contém o assembly que define o tipo que você está usando.

## <a name="see-also"></a>Veja também

- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
- [Referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
- [Solução de Problemas de Referências Quebradas](/visualstudio/ide/troubleshooting-broken-references)
