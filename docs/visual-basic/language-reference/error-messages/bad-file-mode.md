---
title: Modo de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 99b84902ddf032f2ecb6e26400e200bea862dfdf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875154"
---
# <a name="bad-file-mode"></a>Modo de arquivo inválido

As instruções usadas na manipulação do conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto. As possíveis causas incluem:  
  
- Uma `FilePutObject` `FileGetObject` instrução or especifica um arquivo sequencial.  
  
- Uma `Print` instrução especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append` .  
  
- Uma `Input` instrução especifica um arquivo aberto para um modo de acesso diferente de `Input`  
  
- Uma tentativa de gravar em um arquivo somente leitura.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que `FilePutObject` e `FileGetObject` estão apenas se referindo a arquivos abertos para o `Random` ou o `Binary` Access.  
  
- Certifique-se `Print` de especificar um arquivo aberto para o `Output` modo de `Append` acesso ou. Caso contrário, use uma instrução diferente para inserir dados no arquivo ou reabra o arquivo em um modo apropriado.  
  
- Certifique-se `Input` de especificar um arquivo aberto para `Input` . Caso contrário, use uma instrução diferente para inserir dados no arquivo ou reabra o arquivo em um modo apropriado.  
  
- Se você estiver gravando em um arquivo somente leitura, altere o status de leitura/gravação do arquivo ou não tente gravar nele.  
  
- Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem>
- [Solução de problemas: ler e gravar em arquivos de texto](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
