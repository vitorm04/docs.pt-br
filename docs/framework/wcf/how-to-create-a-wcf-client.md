---
title: 'Tutorial: Crie um cliente da Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184108"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Tutorial: Crie um cliente da Windows Communication Foundation

Este tutorial descreve a quarta das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).

A próxima tarefa para criar um aplicativo WCF é criar um cliente recuperando metadados de um serviço WCF. Você usa o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto final mex do serviço. O Visual Studio então gera um arquivo de código-fonte gerenciado para um proxy cliente no idioma que você escolheu. Ele também cria um arquivo de configuração do cliente *(App.config*). Este arquivo permite que o aplicativo cliente se conecte ao serviço em um ponto final.

> [!NOTE]
> Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o recurso **Adicionar referência de serviço** para gerar automaticamente um proxy e um arquivo de configuração associado. No entanto, como os projetos de biblioteca de classe não usam esse arquivo de configuração, você precisa adicionar as configurações no arquivo de configuração gerada ao arquivo *App.config* para o executável que chama a biblioteca de classes.

> [!NOTE]
> Como alternativa, use a [ferramenta ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar a classe proxy e o arquivo de configuração.

O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço. Este procedimento é descrito no [Tutorial: Use um cliente](how-to-use-a-wcf-client.md).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie e configure um projeto de aplicativo de console para o cliente WCF.
> - Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração.

## <a name="create-a-windows-communication-foundation-client"></a>Crie um cliente da Windows Communication Foundation

1. Crie um projeto de aplicativo de console no Visual Studio:

    1. No menu **Arquivo,** selecione **Abrir** > **projeto/solução** e navegue até a solução **GettingStarted** criada anteriormente *(GettingStarted.sln*). Selecione **Abrir**.

    2. No menu **Exibir,** selecione **Solution Explorer**.

    3. Na janela **Solution Explorer,** selecione a solução **GettingStarted** (nó superior e selecione **Adicionar** > **novo projeto** no menu de atalho.

    4. Na janela **Adicionar novo projeto,** no lado esquerdo, selecione a categoria **Windows Desktop** em **Visual C#** ou **Visual Basic**.

    5. Selecione o modelo **Console App (.NET Framework)** e *digite GettingStartedClient* for the **Name**. Selecione **OK**.

2. Adicione uma referência no projeto **GettingStartedClient** à <xref:System.ServiceModel> montagem:

    1. Na janela **Solution Explorer,** selecione a pasta **Referências** no projeto **GettingStartedClient** e selecione **Adicionar referência** no menu de atalho.

    2. Na janela **Adicionar referência,** em **Montagens** no lado esquerdo da janela, **selecione Quadro**.

    3. Encontre e selecione **System.ServiceModel**e escolha **OK**.

    4. Salve a solução selecionando **'Salvar todos'** **do arquivo** > .

3. Adicionar uma referência de serviço ao serviço de calculadora:

   1. Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedClient** e selecione **Adicionar referência** de serviço no menu de atalho.

   2. Na **janela Adicionar referência de serviço,** selecione **Descobrir**.

      O serviço CalculatorService é iniciado e o Visual Studio exibe-o na caixa **Serviços.**

   3. Selecione **CalculadoraService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço. Deixe o **namespace** padrão e escolha **OK**.

      O Visual Studio adiciona um novo item na pasta **Serviços Conectados** no projeto **GettingStartedClient.**

### <a name="servicemodel-metadata-utility-tool"></a>Ferramenta serviceModel Metadata Utility

Os exemplos a seguir mostram como usar opcionalmente a [ferramenta ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe proxy. Esta ferramenta gera o arquivo de classe proxy e o arquivo *App.config.* Os exemplos a seguir mostram como gerar o proxy em C# e Visual Basic, respectivamente:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Arquivo de configuração de cliente

Depois de criar o cliente, o Visual Studio cria o arquivo de configuração **App.config** no projeto **GettingStartedClient,** que deve ser semelhante ao seguinte exemplo:

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

Na seção [ \<system.serviceModel>,](../configure-apps/file-schema/wcf/system-servicemodel.md) observe o [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) elemento>ponto final. O elemento ** &lt;ponto final&gt; ** define o ponto final que o cliente usa para acessar o serviço da seguinte forma:

- Endereço: `http://localhost:8000/GettingStarted/CalculatorService`. O endereço do ponto de extremidade.
- Contrato de `ServiceReference1.ICalculator`serviço: . O contrato de prestação de serviços trata da comunicação entre o cliente WCF e o serviço. O Visual Studio gerou este contrato quando você usou sua função **Add Service Reference.** É essencialmente uma cópia do contrato que você definiu no projeto GettingStartedLib.
- Vinculação: <xref:System.ServiceModel.WSHttpBinding>. A vinculação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Crie e configure um projeto de aplicativo de console para o cliente WCF.
> - Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração para o aplicativo cliente.

Avance para o próximo tutorial para saber como usar o cliente gerado.

> [!div class="nextstepaction"]
> [Tutorial: Use um cliente WCF](how-to-use-a-wcf-client.md)
