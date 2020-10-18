---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162746"
---
# <a name="file-already-open"></a>Arquivo já aberto

Às vezes, um arquivo deve ser fechado antes que outra `FileOpen` ou outra operação possa ocorrer. Entre as possíveis causas desse erro estão:

- Uma operação de modo de saída sequencial `FileOpen` foi executada para um arquivo que já está aberto

- Uma instrução refere-se a um arquivo aberto.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Feche o arquivo antes de executar a instrução.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
