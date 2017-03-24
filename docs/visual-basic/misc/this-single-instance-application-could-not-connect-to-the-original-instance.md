---
title: "Este aplicativo de instância única não pôde se conectar à instância original | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17a3ecd69e0e0974b2a8fc50090097b93dc0def3
ms.lasthandoff: 03/13/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Este aplicativo de instância única não pôde se conectar à instância original
Este aplicativo de instância única não pôde se conectar à instância original. Algumas das possíveis causas para esse problema são as seguintes:  
  
-   A instância original parou de responder.  
  
-   O aplicativo não tem permissões para criar objetos kernel. Para obter mais informações sobre objetos kernel, consulte [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).  
  
     O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária. Por exemplo, o nome de base poderia ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Para corrigir esse erro ao desenvolver o aplicativo  
  
1.  Verifique se o aplicativo não entra em um estado sem resposta.  
  
2.  Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.  
  
3.  Reinicie a instância original do aplicativo.  
  
4.  Reinicie o computador para limpar qualquer processo que possa estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.  
  
5.  Observe as circunstâncias nas quais o erro ocorreu e telefone o Atendimento Microsoft.  
  
## <a name="see-also"></a>Consulte também  
 [NIB: Como: Especificar comportamento de instâncias para um aplicativo (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Noções básicas do depurador](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)   
 [Acessibilidade e suporte a produtos PAVEOVER](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
