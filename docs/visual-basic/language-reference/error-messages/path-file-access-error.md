---
title: Erro ao acessar arquivo de caminho | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ac730bac76540331206daebe600445ca54cc15a9
ms.lasthandoff: 03/13/2017

---
# <a name="pathfile-access-error"></a>Erro de acesso ao demarcador/arquivo
Durante uma operação de acesso a arquivos ou acesso ao disco, o sistema operacional não pôde fazer uma conexão entre o caminho e o nome do arquivo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que a especificação de arquivo está formatada corretamente. Um nome de arquivo pode conter um (absoluto) totalmente qualificado ou relativo ao caminho. Um caminho totalmente qualificado inicia com o nome da unidade (se o caminho estiver em outra unidade) e lista o caminho específico da raiz no arquivo. Qualquer caminho que não é totalmente qualificado é relativo a unidade atual e o diretório.  
  
2.  Certifique-se de que você não tentou salvar um arquivo que substituiria um arquivo somente leitura existente. Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.  
  
3.  Verifique se você não tentou abrir um arquivo somente leitura no sequencial`Output`ou `Append` modo. Se esse for o caso, abra o arquivo no `Input` modo ou alterar o atributo somente leitura do arquivo.  
  
4.  Verifique se você não tentou alterar uma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto dentro de um banco de dados ou documento.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
