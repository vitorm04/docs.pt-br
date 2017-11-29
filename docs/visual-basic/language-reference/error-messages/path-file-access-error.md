---
title: Erro ao acessar arquivo de caminho
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>Erro de acesso ao demarcador/arquivo
Durante uma operação de acesso a arquivos ou o acesso ao disco, o sistema operacional não pôde fazer uma conexão entre o caminho e o nome do arquivo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que a especificação de arquivo está formatada corretamente. Um nome de arquivo pode conter um (absoluto) totalmente qualificado ou relativo ao caminho. Um caminho totalmente qualificado inicia com o nome da unidade (se o caminho está em outra unidade) e lista o caminho específico da raiz para o arquivo. Qualquer caminho que não é totalmente qualificado é relativo a unidade atual e a pasta.  
  
2.  Certifique-se de que você não tentou salvar um arquivo que substitua um arquivo existente de somente leitura. Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.  
  
3.  Certifique-se de que não houve tentativa de abrir um arquivo somente leitura em sequencial `Output` ou `Append` modo. Se esse for o caso, abra o arquivo no `Input` modo ou alterar o atributo somente leitura do arquivo.  
  
4.  Certifique-se de que não houve tentativa de alterar um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projeto dentro de um banco de dados ou documento.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
