---
title: 'Como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 06d4d4f6687979f4fd54e919ca6f236a5b5402e8
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843002"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente
O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] apresenta uma melhor integração entre serviços Web e fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho de primeiro contrato. A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro. A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato.  
  
> [!NOTE]
>  Este tópico fornece orientação passo a passo sobre como criar um serviço de fluxo de trabalho de primeiro contrato. Para obter mais informações sobre o desenvolvimento de serviço de fluxo de trabalho de primeiro contrato, consulte [desenvolvimento de serviço de fluxo de trabalho de primeiro contrato](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Criando o projeto de fluxo de trabalho  
  
1.  No Visual Studio, selecione **arquivo**, **novo projeto**. Selecione o **WCF** nó sob o **C#** nó no **modelos** de árvore e, em seguida, selecione o **aplicativo de serviço de fluxo de trabalho WCF** modelo.  
  
2.  Nomeie o novo projeto `ContractFirst` e clique em **Okey**.  
  
### <a name="creating-the-service-contract"></a>Criando o contrato de serviço  
  
1.  Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **Add**, **Novo Item...** . Selecione o **código** nó à esquerda e o **classe** modelo à direita. Nomeie a nova classe `IBookService` e clique em **Okey**.  
  
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
  
4.  Compile o projeto pressionando **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Importando o contrato de serviço  
  
1.  Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **contrato de serviço de importação**. Sob  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**. Clique em **OK**.  
  
2.  Uma caixa de diálogo abrirá, alertando-o de que a operação foi concluída com êxito e que as atividades geradas serão exibidas na caixa de ferramentas depois que você compilar o projeto. Clique em **OK**.  
  
3.  Compile o projeto pressionando **Ctrl + Shift + B**, de modo que as atividades importadas aparecerão na caixa de ferramentas.  
  
4.  Na **Gerenciador de soluções**, abra Service1.xamlx. O serviço de fluxo de trabalho aparecerá no designer.  
  
5.  Selecione o **sequência** atividade. Na janela Propriedades, clique o **...** botão de **ImplementedContract** propriedade. No **Editor de coleção do tipo** janela que aparece, clique no **tipo** lista suspensa e selecione o **procurar tipos...** entrada. No **navegue e selecione um tipo .NET** caixa de diálogo, em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**. Clique em **OK**. No **Editor de coleção do tipo** caixa de diálogo, clique em **Okey**.  
  
6.  Selecione e exclua as **ReceiveRequest** e **SendResponse** atividades.  
  
7.  Na caixa de ferramentas, arraste um **Buy_ReceiveAndSendReply** e uma **Checkout_Receive** atividade para o **Sequential Service** atividade.
