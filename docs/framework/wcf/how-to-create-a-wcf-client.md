---
title: 'Tutorial: Criar um cliente do Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: a16a0ccabfd0f9fbe69db1ea88d4613185f3c1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174363"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Tutorial: Criar um cliente do Windows Communication Foundation

Este tutorial descreve o quarto de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).

A próxima tarefa para a criação de um aplicativo WCF é criar um cliente recuperando metadados de um serviço WCF. Usar o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto de extremidade MEX do serviço. Em seguida, o Visual Studio gera um arquivo de código fonte gerenciado para um proxy de cliente na linguagem escolhida. Ele também cria um arquivo de configuração do cliente (*App. config*). Esse arquivo permite que o aplicativo cliente conectar-se para o serviço em um ponto de extremidade. 

> [!NOTE]
> Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o **adicionar referência de serviço** recurso para gerar automaticamente um proxy e um arquivo de configuração associado. No entanto, como projetos de biblioteca de classe não usam esse arquivo de configuração, você precisará adicionar as configurações no arquivo de configuração gerado para o *App. config* arquivo para o executável que chama a biblioteca de classes.

> [!NOTE]
> Como alternativa, use o [ferramenta de utilitário de metadados ServiceModel](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar o arquivo de classe e a configuração de proxy.

O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço. Esse procedimento é descrito na [Tutorial: Usar um cliente](how-to-use-a-wcf-client.md).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Criar e configurar um projeto de aplicativo de console para o cliente do WCF.
> - Adicione uma referência de serviço para o serviço do WCF para gerar os arquivos de classe e a configuração de proxy.

## <a name="create-a-windows-communication-foundation-client"></a>Criar um cliente do Windows Communication Foundation

1. Crie um projeto de aplicativo de console no Visual Studio: 

    1. Dos **arquivo** menu, selecione **abra** > **projeto/solução** e navegue até o **GettingStarted** solução você criado anteriormente (*GettingStarted.sln*). Selecione **Abrir**.

    2. Dos **modo de exibição** menu, selecione **Gerenciador de soluções**.

    3. No **Gerenciador de soluções** janela, selecione a **GettingStarted** solução (nó superior) e, em seguida, selecione **Add** > **denovoprojeto** no menu de atalho. 
    
    4. No **adicionar novo projeto** janela, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual C#**  ou **Visual Basic**. 

    5. Selecione o **aplicativo de Console (.NET Framework)** modelo e insira *GettingStartedClient* para o **nome**. Selecione **OK**.

2. Adicionar uma referência na **GettingStartedClient** do projeto para o <xref:System.ServiceModel> assembly: 

    1.  No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedClient** do projeto e, em seguida, selecione **Add Reference** no menu de atalho. 

    2. No **adicionar referência** janela, em **Assemblies** no lado esquerdo da janela, selecione **Framework**.
    
    3. Localize e selecione **System. ServiceModel**e, em seguida, escolha **Okey**. 

    4. Salve a solução selecionando **arquivo** > **Salvar tudo**.

3. Adicione uma referência de serviço para o serviço da Calculadora:

   1. No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedClient** do projeto e, em seguida, selecione **adicionar referência de serviço**  no menu de atalho.

   2. No **adicionar referência de serviço** janela, selecione **Discover**.

      O CalculatorService serviço é iniciado e o Visual Studio exibe-o na **Services** caixa.

   3. Selecione **CalculatorService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço. Deixe o padrão **Namespace** e escolha **Okey**.

      O Visual Studio adiciona um novo item sob o **serviços conectados** pasta o **GettingStartedClient** projeto. 

### <a name="servicemodel-metadata-utility-tool"></a>Ferramenta Utilitário de metadados de ServiceModel

Os exemplos a seguir mostram como usar opcionalmente a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe de proxy. Essa ferramenta gera o arquivo de classe de proxy e o *App. config* arquivo. Os exemplos a seguir mostram como gerar o proxy no C# e Visual Basic, respectivamente:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Arquivo de configuração do cliente

Depois de criar o cliente, o Visual Studio cria o **App. config** arquivo de configuração do **GettingStartedClient** projeto, que deve ser semelhante ao exemplo a seguir:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

Sob o [ \<System. ServiceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) seção, observe o [ \<ponto de extremidade >](../configure-apps/file-schema/wcf/endpoint-element.md) elemento. O **&lt;ponto de extremidade&gt;** elemento define o ponto de extremidade que o cliente usa para acessar o serviço da seguinte maneira:
- Endereço: `http://localhost:8000/GettingStarted/CalculatorService`. O endereço do ponto de extremidade.
- Contrato de serviço: `ServiceReference1.ICalculator`. O contrato de serviço gerencia a comunicação entre o cliente do WCF e o serviço. Visual Studio gerado esse contrato quando você usou seu **adicionar referência de serviço** função. Ele é essencialmente uma cópia do contrato que você definiu no projeto GettingStartedLib. 
- Associação: <xref:System.ServiceModel.WSHttpBinding>. A associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Criar e configurar um projeto de aplicativo de console para o cliente do WCF.
> - Adicione uma referência de serviço para o serviço do WCF para gerar os arquivos de classe e a configuração de proxy para o aplicativo cliente.

Avance para o próximo tutorial para aprender a usar o cliente gerado.

> [!div class="nextstepaction"]
> [Tutorial: Usar um cliente WCF](how-to-use-a-wcf-client.md)
