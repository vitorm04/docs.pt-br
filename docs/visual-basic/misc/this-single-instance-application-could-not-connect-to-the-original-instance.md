---
title: Este aplicativo de instância única não pôde se conectar à instância original
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198133"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Este aplicativo de instância única não pôde se conectar à instância original
Este aplicativo de instância única não pôde se conectar à instância original. Algumas das possíveis causas para esse problema são as seguintes:  
  
- A instância original parou de responder.  
  
- O aplicativo não tem permissões para criar objetos kernel. Para obter mais informações sobre objetos kernel, consulte [mutexes](../../standard/threading/mutexes.md).  
  
     O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária. Por exemplo, o nome de base pode ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Para corrigir esse erro ao desenvolver o aplicativo  
  
1. Verifique se o aplicativo não entra em um estado sem resposta.  
  
2. Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.  
  
3. Reinicie a instância original do aplicativo.  
  
4. Reinicie o computador para limpar qualquer processo que possa estar usando o recurso necessário para se conectar ao aplicativo de instância original.  
  
5. Observe as circunstâncias em que o erro ocorreu e telefone para o atendimento Microsoft.  
  
## <a name="see-also"></a>Consulte também

- [Noções básicas do depurador](/visualstudio/debugger/debugger-feature-tour)
