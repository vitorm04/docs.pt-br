---
title: Kit de ferramentas de Ruleset externo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fbac6bf8be169aca8ad61c69b8d024f44928d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="external-ruleset-toolkit"></a>Kit de ferramentas de Ruleset externo
Normalmente quando as regras são usadas em um aplicativo de fluxo de trabalho, as regras são parte do assembly. Em algumas situações, convém manter o RuleSets separada do assembly de modo que eles possam ser atualizados sem recriar e implantar o assembly de fluxo de trabalho. Este exemplo permite que você gerencie e edite RuleSets em uma base de dados e acesse o RuleSets de um fluxo de trabalho em tempo de execução. Isso permite que instâncias em execução de fluxo de trabalho para inserir automaticamente alterações de RuleSet.  
  
 O exemplo externo do kit de ferramentas de RuleSet contém uma ferramenta baseada em Windows que você pode usar para gerenciar e editar versões de RuleSet em uma base de dados. Ele também inclui uma atividade e um serviço de hospedagem para executar essas regras.  
  
> [!NOTE]
>  Este exemplo requer [Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=96181).  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] fornece um editor de RuleSet como parte do Windows Workflow Foundation (WF). Você pode iniciar o editor clicando duas vezes na atividade de `Policy` em um fluxo de trabalho; serializa o objeto definido de RuleSet para o arquivo de .rules associado com o fluxo de trabalho (uma atividade de `Policy` executa uma instância de RuleSet contra o fluxo de trabalho). O arquivo de .rules é compilado no assembly como um recurso quando você compila o projeto de fluxo de trabalho.  
  
 Componentes deste exemplo incluem:  
  
-   Uma ferramenta de interface gráfica do usuário de RuleSet que você pode usar para editar e gerenciar versões de RuleSet na base de dados.  
  
-   Um serviço de RuleSet que é configurado no aplicativo host e acesse RuleSets de base de dados.  
  
-   Uma atividade de `ExternalPolicy` que é um RuleSet de serviço de RuleSet e executa o RuleSet contra o fluxo de trabalho.  
  
 A interação de componentes é mostrada na figura 1. As seções a seguir descrevem cada componente.  
  
 ![Visão geral conceitual de exemplo de RuleSet externo](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Figure 1: Visão geral de exemplo  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>Ferramenta de RuleSet  
 Uma tela da ferramenta de RuleSet é mostrada na figura 2. Do **regra repositório** menu, você pode carregar o conjunto de regras disponíveis do banco de dados e salvar os conjuntos de regras modificados no armazenamento. Um arquivo de configuração do aplicativo fornece uma cadeia de caracteres de conexão de base de dados para o base de dados de RuleSet. Quando você inicia a ferramenta, carrega automaticamente o RuleSets de base de dados configurado.  
  
 ![Saída de exemplo do Kit de ferramentas de RuleSet externa](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Figure 2: Navegador de RuleSet  
  
 A ferramenta de RuleSet aplica o versão e números de versão secundária ao RuleSets, permitindo que você mantém simultaneamente e versões de armazenamento várias (a ferramenta não fornecer nenhum bloqueio ou outros recursos de gerenciamento de configuração além do recurso de controle de versão). Usando a ferramenta, você pode criar novas versões de RuleSet ou excluir versões existentes. Quando você clica em **novo**, a ferramenta cria um novo nome de conjunto de regras e aplica-se a versão 1.0. Quando você copiar uma versão, a ferramenta cria uma cópia da versão de RuleSet selecionada, incluindo as regras contidas, e atribuir novos, números de versão exclusivos. Esses números de versão são baseados em números de versão de RuleSets existente. Você pode alterar o nome e números de versão de RuleSet usando os campos associados no formulário.  
  
 Quando você clica em **editar regras de**, o editor de conjunto de regras é iniciado, conforme mostrado na Figura 3.  
  
 ![Saída de exemplo do Kit de ferramentas de RuleSet externo](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Figure 3: Editor de RuleSet  
  
 Este é novamente hospedar da caixa de diálogo de editor que é parte de suplementos do Windows Workflow Foundation [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] . Fornece a mesma funcionalidade, incluindo suporte Intellisense. As regras são criadas em relação a um tipo de destino (como um fluxo de trabalho) que está associado com o conjunto de regras na ferramenta. Quando você clica em **procurar** na caixa de diálogo ferramentas principal, o **seletor de tipo de fluxo detrabalho/** caixa de diálogo for exibida, conforme mostrado na Figura 4.  
  
 ![Fluxo de trabalho &#47; Seleção de tipo](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Figure 4: Seletor de fluxo de trabalho/tipo  
  
 Você pode usar o **seletor de tipo de fluxo detrabalho/** caixa de diálogo para especificar um assembly e um tipo específico dentro desse assembly. Esse tipo é o tipo de destino com que as regras são criadas (e execução). Em muitos casos, o tipo de destino é um fluxo de trabalho ou qualquer outro tipo de atividade. No entanto, você pode executar um RuleSet contra qualquer tipo .NET.  
  
 O caminho para o arquivo de assembly e o tipo `name are stored with the` RuleSet no banco de dados, para que quando o conjunto de regras é recuperado do banco de dados, a ferramenta tenta carregar automaticamente o tipo de destino.  
  
 Quando você clica em **Okey** no **seletor de tipo de fluxo detrabalho/** caixa de diálogo, ele valida o tipo selecionado no conjunto de regras para garantir que o tipo de destino tem todos os membros referenciados pelas regras. Erros são mostrados em um **erros de validação** caixa de diálogo (consulte a Figura 5). Você pode optar por continuar com a alteração, apesar de erros ou clique em **Cancelar**. Do **ferramentas** menu na caixa de diálogo ferramentas principal, você pode clicar em **validar** para validar novamente a versão do conjunto de regras em relação a atividade de destino.  
  
 ![Erros de validação de exemplo de RuleSet externo](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Figure 5: Erros de validação  
  
 Do **dados** menu na ferramenta, você pode importar e exportar conjuntos de regras. Quando você clica em **importação**, aparece uma caixa de diálogo Seletor de arquivos, na qual você pode selecionar um arquivo. rules. Isso pode ou não um arquivo criado inicialmente em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. O arquivo de .rules deve conter uma instância serializada de `RuleDefinitions` que contém uma coleção de condições e uma coleção de RuleSets. A ferramenta não usar a coleção das circunstâncias, mas usa o formato de `RuleDefinitions` .rules para permitir a interação com o ambiente de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] .  
  
 Depois de selecionar um arquivo. Rules, um **seletor de RuleSet** caixa de diálogo é exibida (consulte a Figura 6). Você pode usar a caixa de diálogo para selecionar o RuleSets do arquivo que você deseja importar (a opção especificar qualquer RuleSets). RuleSets no arquivo de .rules não tem números de versão, porque o controle de versão em um projeto de WF é o mesmo que a versão do assembly. Durante o processo de importação, a ferramenta atribui automaticamente o próximo número de versão primária (que pode ser alterada depois de importar); Você pode ver os números de versão atribuído a **seletor de RuleSet** lista.  
  
 Para cada RuleSet importa, tentativas da ferramenta de localizar o tipo associado bin \ debug no local do arquivo de .rules (se existir), com base nos membros usados no RuleSet. Se a ferramenta encontrar vários tipos de correspondência, tentar escolha um tipo com base em uma correspondência entre o nome de arquivo .rules e o nome do tipo (por exemplo, o tipo de `Workflow1` corresponde a Workflow1.rules). Se as correspondências múltiplas existirem, você será solicitado para selecionar o tipo. Se esse mecanismo de identificação automática não conseguir localizar um assembly ou um tipo de correspondência, após a importação, você pode clicar **procurar** na caixa de diálogo ferramenta principal para navegar para o tipo associado.  
  
 ![Seletor de RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Figure 6: Seletor de RuleSet  
  
 Quando você clica em **exportar dados** no menu de ferramentas principal, o **seletor de RuleSet** caixa de diálogo aparece novamente, do qual você pode determinar o conjunto de regras do banco de dados que deve ser exportado. Quando você clica em **Okey**, um **salvar arquivo** caixa de diálogo for exibida, na qual você pode especificar o nome e o local do arquivo. Rules resultante. Porque o arquivo de .rules não contém informações de versão, você pode selecionar apenas uma versão de RuleSet com um determinado nome de RuleSet.  
  
## <a name="policyfromservice-activity"></a>Atividade de PolicyFromService  
 O código para atividades de `PolicyFromService` é simples. Funciona bem como a atividade de `Policy` fornecida com o WF, mas em vez de recuperar o destino RuleSet do arquivo de .rules, chama um serviço de hospedagem para obter a instância de RuleSet. Execute o RuleSet contra a instância de atividade de fluxo de trabalho de raiz.  
  
 Para usar a atividade em um fluxo de trabalho, adicione uma referência a `PolicyActivities` e assemblies de `RuleSetService` do fluxo de trabalho projeto. Consulte o procedimento no final deste tópico para uma discussão sobre como adicionar a atividade a caixa de ferramentas.  
  
 Após a atividade colocado no fluxo de trabalho, você deve fornecer o nome de RuleSet a ser executado. Você pode inserir o nome como um valor literal, ou o associar a uma variável de fluxo de trabalho ou propriedade de outra atividade. Opcionalmente, você pode digitar números de versão para o RuleSet específico que deve ser executado. Se você deixar o valor padrão de 0 para os números de versão principal e secundário, o número de versão do último na base de dados é fornecida automaticamente para atividades.  
  
## <a name="ruleset-service"></a>Serviço de RuleSet  
 O serviço é responsável por recuperar a versão especificada de RuleSet de base de dados dados e a atividade de chamada. Como discutido anteriormente, se os valores de versão principal e versão secundária passados na chamada de `GetRuleSet` são ambos 0, o serviço recupera a versão mais recente. Neste ponto, não há cachê de definições ou de instâncias de RuleSet; da mesma forma, não há nenhum recurso para marcar versões de RuleSet como “implantado para” diferenciá-las de RuleSets em andamento.  
  
 O base de dados a ser acessado pelo serviço deve ser configurado no host que usa um arquivo de configuração do aplicativo.  
  
#### <a name="to-run-the-tool"></a>Para executar a ferramenta  
  
1.  A pasta que configura a tabela de RuleSet usado pela ferramenta e o serviço contém um arquivo de Setup.sql. Você pode executar o arquivo em lotes de Setup.cmd para criar o base de dados de regras em SQL express e configurar a tabela de RuleSet.  
  
2.  Se você editar o arquivo em lotes ou o Setup.sql e os especifica para não usar o SQL express ou não coloque a tabela em uma base de dados chamado algo diferente `Rules`, os arquivos de configuração do aplicativo na ferramenta de RuleSet e projetos de `UsageSample` devem ser editados com a mesma informações.  
  
3.  Depois que você execute o script de Setup.sql, você pode criar a solução de `ExternalRuleSetToolkit` e em iniciar a ferramenta de RuleSet de projeto de ExternalRuleSetTool.  
  
4.  A solução sequencial do aplicativo de console do fluxo de trabalho `RuleSetToolkitUsageSample` inclui um fluxo de trabalho de exemplo. O fluxo de trabalho consiste em uma atividade de `PolicyFromService` e duas variáveis, `orderValue` e `discount`, com que o destino RuleSet executa.  
  
5.  Para usar o exemplo, crie a solução de `RuleSetToolkitUsageSample` . No menu principal da ferramenta conjunto de regras, clique em **importação de dados** e apontar para o arquivo DiscountRuleSet.rules na pasta RuleSetToolkitUsageSample. Clique o **economia de armazenamento Rule** opção de menu para salvar o conjunto de regras importado para o banco de dados.  
  
6.  Porque o assembly de `PolicyActivities` é referenciado de projeto de fluxo de trabalho de exemplo, a atividade de `PolicyFromService` aparece no fluxo de trabalho. , No entanto, não aparece na caixa de ferramentas por padrão. Para adicioná-lo à caixa de ferramentas, faça o seguinte:  
  
    -   A caixa de ferramentas e selecione **escolher itens** (Isso pode demorar um pouco).  
  
    -   Quando o **escolher itens da caixa de ferramentas** caixa de diálogo for exibida, clique no **atividades** guia.  
  
    -   Navegue até o `PolicyActivities` assembly no `ExternalRuleSetToolkit` solução e clique em **abrir**.  
  
    -   Certifique-se de que o `PolicyFromService` atividade selecionada no **escolher itens da caixa de ferramentas** caixa de diálogo e clique **Okey**.  
  
    -   A atividade agora deve aparecer na caixa de ferramentas de **RuleSetToolkitUsageSample componentes** categoria.  
  
7.  O serviço de RuleSet já está configurado no host do aplicativo de console usando a seguinte declaração em Module.vb.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Você também pode configurar o serviço no host que usa um arquivo de configuração; consulte a documentação SDK para obter detalhes.  
  
9. Um arquivo de configuração do aplicativo é adicionado ao projeto de fluxo de trabalho especificar a cadeia de conexão para o base de dados é usado pelo serviço. Isso deve ser a mesma cadeia de conexão usada pela ferramenta de RuleSet, apontando para a base de dados que contém a tabela de RuleSet.  
  
10. Agora você pode executar o projeto de `RuleSetToolkitUsageSample` como você faria qualquer outro aplicativo de console do fluxo de trabalho. Pressione F5 ou Ctrl+F5 dentro de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ou execute o arquivo de RuleSetToolkitUsageSample.exe diretamente.  
  
    > [!NOTE]
    >  Você deve fechar a ferramenta de RuleSet para recompilar o exemplo de uso, porque a ferramenta carrega o assembly de exemplo de uso.