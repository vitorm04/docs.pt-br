---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 111e7aa4164d9fc811ebe3f5efb196df77d1ded0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Este exemplo demonstra o uso e configuração de propriedades elevadas no armazenamento de instância de fluxo de trabalho SQL. O armazenamento de instância de fluxo de trabalho do SQL é uma implementação SQL- base de um armazenamento de instância. Permite que uma instância salve o estado e carrega o estado para e de um base de dados SQL Server ou do SQL Server Express. O recurso de extensibilidade de armazenamento permite que o usuário defina as propriedades que são armazenadas no armazenamento de instância. Essas propriedades são exibidas em uma exibição promovida propriedades que permite que o usuário possa ver para eles.  
  
 Esse exemplo consiste em um fluxo de trabalho que implementa um serviço de contagem. Uma vez que o método inicial do serviço é chamado, o serviço conta 0 a 29. O contador é incrementado uma vez a cada 2 segundos. Após cada contagem, o fluxo de trabalho persiste. O valor do contador atual é armazenado no armazenamento de instância como uma propriedade promovida.  
  
 O fluxo de trabalho de contagem dica é hospedado por um host de Serviço de Fluxo de Trabalho. O método de `Main` do programa executa as seguintes ações:  
  
-   Cria uma instância de host de Serviço de Fluxo de Trabalho que hospeda o fluxo de trabalho de contagem e define os pontos de extremidade em que o fluxo de trabalho de contagem pode ser alcançado.  
  
-   Define um comportamento do armazenamento de instância de fluxo de trabalho SQL, que é usado para configurar o armazenamento de instância de fluxo de trabalho SQL. O armazenamento é instruído para manipular `CountStatus` como uma propriedade promovida.  
  
-   Cria um cliente que chama o método inicial do fluxo de trabalho de contagem.  
  
 O programa é iniciado uma vez, o contador inicia automaticamente a contagem. Observe que pode levar alguns segundos para carregar a instância e configurar o armazenamento de instância de fluxo de trabalho SQL.  
  
 Para elevar o valor do contador como uma propriedade personalizada, as seguintes etapas devem ser executadas:  
  
1.  A classe `CounterStatus` define uma extensão da instância do tipo <xref:System.Activities.Persistence.PersistenceParticipant>, que é usado por atividades para fornecer variáveis de estado. `Count` é definido como um valor somente gravação. Quando uma instância de fluxo de trabalho chega a um ponto de persistência, a extensão de instância salva a propriedade de `Count` na coleção de dados de persistência.  
  
2.  Ao criar o armazenamento de instância, uma nova propriedade, `CountStatus`, é definida com o método de `store.Promote()` .  
  
3.  A atividade de `SaveCounter` de fluxo de trabalho atribui o valor do contador atual para o campo status de `Count` .  
  
### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Crie o base de dados da instância.  
  
    1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Navegue para o diretório de exemplo (\ \ WF básico persistência SqlStoreExtensibility \ \ \ CS) e a CreateInstanceStore.cmd executado no prompt de comando de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] .  
  
        > [!WARNING]
        >  O script de CreateInstanceStore.cmd tentar criar o base de dados na instância padrão do SQL Server 2008 Express. Se você deseja instalar o base de dados em uma instância diferente, modifique o script para fazer isso.  
  
2.  Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e carregar a solução de SqlStoreExtensibility.sln e construa-a pressionando CTRL+SHIFT+B.  
  
    > [!WARNING]
    >  Se você instalou o base de dados em uma instância não padrão do SQL Server, atualizar a cadeia de conexão no código antes de criar a solução.  
  
3.  Executar o exemplo com privilégios de administrador, navegue até o diretório do projeto bin (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) em [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], clicando duas vezes SqlStoreExtensibility.exe e selecionando **executar como Administrador**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Para verificar o exemplo está funcionando corretamente  
  
1.  Use o SQL Server Management Studio para exibir o conteúdo da tabela de instância selecionando **bancos de dados**, **InstanceStore**e, em seguida,  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** no Pesquisador de objetos, clique com botão direito **System.ServiceModel.Activities.DurableInstancing.InstanceTable** e selecione  **Selecione os primeiros 1.000 linhas**. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio, consulte [apresentando o SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Observe as instâncias de fluxo de trabalho listadas.  
  
3.  Em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , execute o script de QueryInstanceStore.cmd localizado no diretório de exemplo (\ \ WF básico \ \ SqlStoreExtensibility persistência).  
  
4.  Observe o valor do contador exibido em **CountStatus**.  
  
5.  Execute o script algumas vezes para ver o **CountStats** alteração de valor.  
  
6.  Pressione ENTER para encerrar o aplicativo de fluxo de trabalho.  
  
### <a name="to-uninstall-the-sample"></a>Para desinstalar o exemplo  
  
1.  Remova a base de dados da instância executando o script de RemoveInstanceStore.cmd localizado no diretório de exemplo (\ \ WF básico \ \ SqlStoreExtensibility persistência).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Consulte também  
 [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
