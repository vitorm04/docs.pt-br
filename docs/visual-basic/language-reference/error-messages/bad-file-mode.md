---
title: Modo de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 9a59faf1b6f845858e36efcabdf0758e41ad75dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619743"
---
# <a name="bad-file-mode"></a>Modo de arquivo inválido
Instruções usadas na manipulação de conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto. Possíveis causas incluem:  
  
- Um `FilePutObject` ou `FileGetObject` declaração especifica um arquivo sequencial.  
  
- Um `Print` declaração especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.  
  
- Um `Input` declaração especifica um arquivo aberto para um modo de acesso diferente de `Input`  
  
- Uma tentativa de gravar em um arquivo somente leitura.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se `FilePutObject` e `FileGetObject` estiver apenas fazendo referência a arquivos abertos para `Random` ou `Binary` acesso.  
  
- Certifique-se `Print` Especifica um arquivo aberto para qualquer um `Output` ou `Append` modo de acesso. Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.  
  
- Certifique-se `Input` Especifica um arquivo aberto para `Input`. Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.  
  
- Se você estiver escrevendo em um arquivo somente leitura, altere o status de leitura/gravação do arquivo ou não tentar gravar nele.  
  
- Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileSystem>
- [Solução de problemas: Lendo e gravando em arquivos de texto](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
