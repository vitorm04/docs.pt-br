---
title: Erro ao acessar arquivo de caminho
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799171"
---
# <a name="pathfile-access-error"></a>Erro de acesso ao demarcador/arquivo
Durante uma operação de acesso a arquivos ou o acesso ao disco, o sistema operacional não pôde fazer uma conexão entre o caminho e o nome do arquivo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se que a especificação de arquivo está formatada corretamente. Um nome de arquivo pode conter um (absoluto) totalmente qualificado ou relativo ao caminho. Um caminho totalmente qualificado começa com o nome da unidade (se o caminho está em outra unidade) e o caminho explícito da raiz no arquivo de lista. Qualquer caminho que não é totalmente qualificado é relativa à unidade atual e diretório.  
  
2. Certifique-se de que você não tentou salvar um arquivo que substitua um arquivo somente leitura existente. Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.  
  
3. Verifique se você não tentou abrir um arquivo somente leitura no sequencial `Output` ou `Append` modo. Se esse for o caso, abra o arquivo no `Input` modo ou alterar o atributo somente leitura do arquivo.  
  
4. Certifique-se de que não houve tentativa de alterar um projeto do Visual Basic dentro de um banco de dados ou documento.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
