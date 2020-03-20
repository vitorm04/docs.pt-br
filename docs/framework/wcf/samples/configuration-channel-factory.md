---
title: Factory do canal de configuração
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183945"
---
# <a name="configuration-channel-factory"></a>Factory do canal de configuração
Esta amostra abrange o <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>uso do . O <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite o gerenciamento central da configuração do cliente WCF. Isso também pode ser útil em cenários nos quais a configuração é selecionada ou alterada após o tempo de carregamento do domínio do aplicativo.

## <a name="demonstrates"></a>Demonstra
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Discussão
 Esta amostra mostra <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> como usar para adicionar um arquivo de configuração específico a um aplicativo cliente, sem ter que usar o arquivo de configuração de aplicativo padrão.

 A amostra consiste em dois projetos. O primeiro projeto é um serviço simples que funciona para responder às mensagens vindas dos clientes. O segundo projeto é um aplicativo <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> cliente <xref:System.Configuration.ExeConfigurationFileMap> que constrói dois objetos usando um para o arquivo de configuração Test.config e os usa para se comunicar com o serviço. Ambos os clientes se comunicam com o serviço usando a configuração especificada em Test.config.

 O código a seguir adiciona um arquivo de configuração personalizado a um aplicativo cliente.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Abra o Visual Studio 2012 com privilégios de administrador.

2. Clique com o botão direito do mouse na solução ConfigurationChannelFactory (2 projetos) e, em seguida, selecione **Propriedades**.

3. Em **Propriedades Comuns,** selecione **Projeto de Inicialização**e clique em **Vários projetos de inicialização**.

4. Mova o projeto **Serviço** para o início da lista, com a **Ação 'Iniciar'** e, em seguida, mova o projeto **Cliente** após o projeto **Serviço,** também com a **Ação 'Start',** para que o projeto **Cliente** seja executado após o projeto **Serviço.**

5. Clique **em OK**e pressione F5 (ou CTRL+F5) para executar a amostra.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
