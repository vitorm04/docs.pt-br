---
title: "Este aplicativo de instância única não pôde se conectar à instância original"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Este aplicativo de instância única não pôde se conectar à instância original
Este aplicativo de instância única não pôde se conectar à instância original. Algumas das possíveis causas para esse problema são as seguintes:  
  
-   A instância original parou de responder.  
  
-   O aplicativo não tem permissões para criar objetos kernel. Para obter mais informações sobre objetos de kernel, consulte [Mutexes](../../standard/threading/mutexes.md).  
  
     O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária. Por exemplo, o nome de base poderia ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Para corrigir esse erro durante o desenvolvimento de aplicativo  
  
1.  Verifique se o aplicativo não entrar em um estado sem resposta.  
  
2.  Verifique se o aplicativo tem permissões suficientes para criar objetos de kernel.  
  
3.  Reinicie a instância original do aplicativo.  
  
4.  Reinicie o computador para limpar qualquer processo que possam estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.  
  
5.  Observe as circunstâncias nas quais o erro ocorreu e telefone Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)  

