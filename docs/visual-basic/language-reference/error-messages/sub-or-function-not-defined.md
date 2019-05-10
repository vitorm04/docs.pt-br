---
title: Sub ou função não definida (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 3a56d5596c79900bb5818a6ed7f8736859b5ea15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593193"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou função não definida (Visual Basic)
Um `Sub` ou `Function` deve ser definido para ser chamado. Possíveis causas do erro incluem:  
  
- Digitar incorretamente o nome do procedimento.  
  
- Tentar chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto na **referências** caixa de diálogo.  
  
- Especificando um procedimento que não é visível para o procedimento de chamada.  
  
- Declarando uma rotina de biblioteca de vínculo dinâmico (DLL) do Windows ou a rotina de recurso de código Macintosh que não está no recurso de biblioteca ou código especificado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Certifique-se de que o nome do procedimento esteja escrito corretamente.  
  
2. Localizar o nome do projeto que contém o procedimento que você deseja chamar o **referências** caixa de diálogo. Se não aparecer, clique o **procurar** botão para pesquisar por ele. Marque a caixa de seleção à esquerda do nome do projeto e, em seguida, clique em **Okey**.  
  
3. Verifique o nome da rotina.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
