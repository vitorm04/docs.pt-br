---
title: Configuração interno
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084787"
---
# <a name="built-in-configuration"></a>Configuração interno
Este exemplo demonstra o uso e a configuração da instância de fluxo de trabalho SQL. O armazenamento de instância de fluxo de trabalho do SQL é uma implementação SQL- base de um armazenamento de instância. Permite que uma instância salvar e carrega o estado para e de um base de dados SQL Server ou do SQL Server Express.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para (página de download) Baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Esse exemplo consiste em um fluxo de trabalho que implementa um serviço de contagem. Depois que o método de início do serviço é invocado, o serviço conta 0 a 59. O contador é incrementado uma vez a cada 2 segundos. Após cada contagem, o fluxo de trabalho persiste.  
  
 Os trabalhos de contagem autodescritivos são hospedados por um host serviço de trabalho. O método de `Main` de programa cria uma instância do host serviço de fluxo de trabalho que hospeda o fluxo de trabalho de contagem. Define os pontos de extremidade em que o fluxo de trabalho de contagem pode ser alcançado. Após isso, define um comportamento do armazenamento de instância de fluxo de trabalho SQL, que é usado para configurar o armazenamento de instância de fluxo de trabalho SQL. Em seguida, o programa cria um cliente que chama o método inicial do fluxo de trabalho de contagem.  
  
 O programa é iniciado uma vez, o contador inicia automaticamente a contagem. Observe que pode levar alguns segundos para carregar a instância e configurar o armazenamento de instância de fluxo de trabalho SQL. Para obter mais informações sobre o armazenamento de instância de fluxo de trabalho, consulte [Store de instância de fluxo de trabalho do SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 O exemplo consiste em duas partes:  
  
1.  InstanceStore1 mostra como <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> é configurado usando o código em c (consulte Module.vb).  
  
2.  InstanceStore2 mostra como <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> é configurado usando XML (consulte App.config.)  
  
 As seguintes configurações estão disponíveis para configurar o comportamento de Store de instância de fluxo de trabalho do SQL:  
  
-   Definir `HostLockRenewalPeriod`. Desta vez definem o intervalo com que o host renova o bloqueio de propriedade de instâncias que executa. Informações de bloqueio é armazenada na instância Store. Se a propriedade não é renovada para dois dos intervalos definidos em `HostLockRenewalPeriod`, a instância é considerada abandonada. Se outro <xref:System.ServiceModel.Activities.WorkflowServiceHost> está executando o mesmo fluxo de trabalho e conectado ao mesmo armazenamento de instância (no mesmo computador ou em um computador diferente), recupera essa instância. (A recuperação de instância é fora do escopo para esse exemplo.)  
  
-   Definir `RunnableInstancesDetectionPeriod`. Esse período define o intervalo em que o host ele investiga para as instâncias que se tornaram praticáveis. As instâncias podem ficar praticáveis se qualquer um dos seguintes eventos ocorrem:  
  
    -   Um timer durável (<xref:System.Activities.Statements.Delay>expira.)  
  
    -   Outro host não possui sua pulsação de `HostLockRenewal` (por exemplo, devido a uma falha do computador) e a instância é recuperado.  
  
-   Definir `InstanceCompletionAction`. Essa propriedade, se definida como `DeleteNothing`, mantenha instâncias concluídas na instância; Store se definida como `DeleteAll`, instâncias for excluído de armazenamento em cima de conclusão. Observe que  
  
    > [!NOTE]
    >  Finalizar o host pressionando ENTER antes que a contagem concluir não concluir a instância de fluxo de trabalho.  
  
-   Definir `InstanceLockedExceptionAction`. Essa configuração define o que um host deve fazer se deseja carregar uma instância que esteja bloqueada por outro host. Existem as seguintes opções:  
  
    -   Se definida como `NoRetry`: Não repita a carga e não retorna `InstanceLockedException` para o host.  
  
    -   Se definida como `BasicRetry`: Manter que experimenta de volta para carregar a instância. As novas tenta são agendadas de acordo com um algoritmo linear simples (por exemplo, repita a cada 5 segundos).  
  
    -   Se definida como `AggressiveRetry`: Manter que experimenta de volta para carregar a instância. As novas tenta são agendadas de acordo com um exponencialmente agressivo desembaraçam do algoritmo.  
  
-   Definir a opção de codificação. Essa configuração define como o estado da instância é armazenado na instância Store de fluxo de trabalho SQL. Existem as seguintes opções:  
  
    -   O estado da instância é compactado usando o algoritmo de compactação de GZip.  
  
    -   O estado da instância não é compactado.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] como um administrador se as permissões estão disponíveis.  
  
2.  Navegue para o diretório de exemplo (\ \ WF básico persistência BuiltInConfiguration \ \ \ CS) e a CreateInstanceStore.cmd executado.  
  
3.  Se os privilégios de administrador não estão disponíveis, crie o login SQL Server. Vá para `Security`, **logons**. Clique com botão direito **logons** e crie um novo logon.  
  
4.  Adicione o usuário ACL a função SQL. Abra **bancos de dados**, **InstanceStore**, **segurança**. Clique com botão direito **os usuários** e selecione **novos usuários**. Defina as **nome de logon** ao usuário criado na etapa anterior. Adicione o usuário para a associação de função de banco de dados **instancestoreusers** (e outros). Observe que o usuário pode existir ainda (por exemplo, dbo de usuário).  
  
5.  Abra o arquivo de InstanceStore.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e crie a solução. CTRL+SHIFT+B pressionando.  
  
6.  Na [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navegue até o diretório do exemplo de bin\debug apropriado (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), clique com botão direito InstanceStore.exe e selecione **executar como administrador**. Este exemplo deve ser executado com privilégios administrativos porque abre um ouvinte de canal.  
  
7.  Se você criou o armazenamento de instância em uma base de dados que não seja uma instalação local do SQL Server Express você deve atualizar a cadeia de conexão caracteres de base de dados (`const string ConnectionString` em Module.vb de projeto InstanceStore1, e o atributo de `connectionString` em App.config do projeto InstanceStore2) no exemplo e recompilar o exemplo.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Para verificar o exemplo está sendo executado corretamente  
  
1.  Quando executar o exemplo, inicie o SQL Server Management Studio.  
  
2.  No **Pesquisador de objetos**, selecione **bancos de dados**, **InstanceStore**, **tabelas**e, em seguida,  **Instancetable**.  
  
3.  Clique com botão direito **InstanceTable** e selecione **selecionar 1000 linhas superiores**.  
  
4.  Observe que há uma nova entrada e que o **expiração de bloqueio** muda a cada 5 segundos, (clique da barra de tarefas **Execute** botão para atualizar a consulta). Isso é uma consequência de definir a **período de renovação de bloqueio de Host** para 5.  
  
5.  Observe que a contagem após concluir, que a entrada na tabela da instância é removida. Isso é uma consequência de definir **ação de conclusão da instância** à **DeleteAll**.  
  
6.  Pressione ENTER para encerrar o aplicativo de host de fluxo de trabalho e observe que o **LockOwnersTable** é excluído.  
  
#### <a name="to-uninstall-the-sample"></a>Para desinstalar o exemplo  
  
1.  Execução RemoveInstanceStore.cmd no diretório de exemplo (\ \ WF básico \ \ BuiltInConfiguration persistência).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
