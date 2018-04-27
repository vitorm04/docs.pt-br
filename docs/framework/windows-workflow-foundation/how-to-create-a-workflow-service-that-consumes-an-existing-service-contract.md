---
title: Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09c3f7656284dd73dd5f50c4ef9f77cd5adcbfe7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente
O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] apresenta uma melhor integração entre serviços Web e fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho de primeiro contrato. A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro. A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato.  
  
> [!NOTE]
>  Este tópico fornece orientação passo a passo sobre como criar um serviço de fluxo de trabalho de primeiro contrato. [!INCLUDE[crabout](../../../includes/crabout-md.md)] desenvolvimento de serviço de fluxo de trabalho do contrato, primeiro, consulte [desenvolvimento de serviço de fluxo de trabalho primeiro contrato](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Criando o projeto de fluxo de trabalho  
  
1.  No Visual Studio, selecione **arquivo**, **novo projeto**. Selecione o **WCF** nó sob o **c#** nó o **modelos** de árvore e selecione o **aplicativo de serviço de fluxo de trabalho WCF** modelo.  
  
2.  Nomeie o novo projeto `ContractFirst` e clique em **Okey**.  
  
### <a name="creating-the-service-contract"></a>Criando o contrato de serviço  
  
1.  Clique com botão direito no projeto no **Solution Explorer** e selecione **adicionar**, **Novo Item...** . Selecione o **código** nó à esquerda e o **classe** modelo à direita. Nomeie a nova classe `IBookService` e clique em **Okey**.  
  
2.  Na parte superior da janela de código que aparece, adicione uma instrução Using a `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Altere a definição de classe de exemplo à seguinte definição da interface.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  Compilar o projeto, pressionando **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Importando o contrato de serviço  
  
1.  Clique com botão direito no projeto no **Solution Explorer** e selecione **contrato de serviço de importação**. Em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**. Clique em **OK**.  
  
2.  Uma caixa de diálogo abrirá, alertando-o de que a operação foi concluída com êxito e que as atividades geradas serão exibidas na caixa de ferramentas depois que você compilar o projeto. Clique em **OK**.  
  
3.  Compilar o projeto, pressionando **Ctrl + Shift + B**, de modo que as atividades importadas serão exibido na caixa de ferramentas.  
  
4.  Em **Solution Explorer**, abra Service1.xamlx. O serviço de fluxo de trabalho aparecerá no designer.  
  
5.  Selecione o **sequência** atividade. Na janela Propriedades, clique o **...** no botão de **ImplementedContract** propriedade. No **Editor de coleção do tipo** janela que aparece, clique no **tipo** suspenso e selecione o **procurar tipos...** entrada. No **procurar e selecione um .net tipo** caixa de diálogo, em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**. Clique em **OK**. No **Editor de coleção do tipo** caixa de diálogo, clique em **Okey**.  
  
6.  Selecione e exclua o **ReceiveRequest** e **SendResponse** atividades.  
  
7.  Na caixa de ferramentas, arraste um **Buy_ReceiveAndSendReply** e um **Checkout_Receive** atividade para o **serviço sequencial** atividade.
