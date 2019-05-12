---
title: Adicionar WCF Web Service Reference
description: Uma visão geral da ferramenta Microsoft WCF Web Service Reference Provider que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta Adicionar Referência de Serviço para projetos do .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 806f6e90aedc669c3a56ce1cde64311bdd4af32c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750498"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Usar a ferramenta WCF Web Service Reference Provider

Ao longo dos anos, muitos desenvolvedores do Visual Studio têm apreciado a produtividade que a ferramenta [**Adicionar Referência de Serviço**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) fornecida quando seus projetos do .NET Framework precisam acessar serviços Web.  A ferramenta **WCF Web Service Reference** é uma extensão de serviço conectado do Visual Studio que fornece uma experiência semelhante à funcionalidade Adicionar Referência de Serviço para projetos do .NET Core e ASP.NET Core. Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL, e gera um arquivo de origem compatível com o .NET Core que contém o código de proxy de cliente do WCF (Windows Communication Foundation) que você pode usar para acessar esse serviço Web.

> [!IMPORTANT]
> Você só deve fazer referência a serviços de uma fonte confiável. A adição de referências de uma fonte não confiável pode comprometer a segurança.

## <a name="prerequisites"></a>Pré-requisitos

* [Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou versões posteriores

## <a name="how-to-use-the-extension"></a>Como usar a extensão

> [!NOTE]
> A opção **WCF Web Service Reference** é aplicável a projetos criados com o uso dos seguintes modelos de projeto:
> * **Visual C#** > **.NET Core**
> * **Visual C#** > **.NET Standard**
> * **Visual C#** > **Web** > **Aplicativo Web ASP.NET Core**

Ao usar o modelo de projeto **Aplicativo Web ASP.NET Core** como um exemplo, este artigo o orienta na adição de uma referência de serviço WCF ao projeto:

1. No Gerenciador de Soluções, clique duas vezes no nó **Serviços Conectados** do projeto (para um projeto do .NET Core ou .NET Standard, essa opção está disponível quando você clica com o botão direito do mouse no nó **Dependências** do projeto no Gerenciador de Soluções).

    A página **Serviços Conectados** é exibida, conforme mostrado na imagem a seguir:

    ![Guia Serviços Conectados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na página **Serviços Conectados**, clique em **Microsoft WCF Web Service Reference Provider**. Isso apresenta o assistente **Configurar a WCF Web Service Reference**:

    ![Guia Ponto de Extremidade do Serviço do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Selecione um serviço.

    3a. Há várias opções de pesquisa de serviços disponíveis no assistente **Configurar a WCF Web Service Reference**:

     * Para pesquisar serviços definidos na solução atual, clique no botão **Descobrir**.
     * Para pesquisar serviços hospedados em um endereço especificado, insira uma URL de serviço na caixa **Endereço** e clique no botão **Ir**.
     * Para selecionar um arquivo WSDL que contenha as informações de metadados do serviço Web, clique no botão **Procurar**.

    3b. Selecione o serviço na lista de resultados da pesquisa na caixa **Serviços**. Se necessário, insira o namespace para o código gerado na caixa de texto **Namespace** correspondente.

    3c. Clique no botão **Avançar** para abrir as páginas **Opções de Tipo de Dados** e **Opções do Cliente**. Como alternativa, clique no botão **Concluir** para usar as opções padrão.

4. O formulário **Opções de Tipo de Dados** permite que você refine as definições de configuração de referência do serviço gerado:

    ![Guia Opções de tipo de dados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > A opção da caixa de seleção **Usar novamente os tipos em assemblies consultados** é útil quando os tipos de dados necessários para a geração de código da referência de serviço são definidos em um dos assemblies referenciados do seu projeto.  É importante reutilizar esses tipos de dados existentes para evitar problemas de conflito de tipo de tempo de compilação ou problemas de tempo de execução.

    Pode haver um atraso enquanto as informações de tipo são carregadas, dependendo do número de dependências do projeto e de outros fatores de desempenho do sistema. O botão **Concluir** será desabilitado durante o carregamento, a menos que a caixa de seleção **Usar novamente os tipos em assemblies consultados** esteja desmarcada.

5. Clique em **Concluir** quando terminar.

Enquanto exibe o andamento, a ferramenta:

* Baixa metadados do serviço WCF.
* Gera o código de referência de serviço em um arquivo chamado *reference.cs* e o adiciona ao seu projeto no nó **Serviços Conectados**.
* Atualiza o arquivo de projeto (.csproj) com as referências de pacote NuGet necessárias para compilar e executar na plataforma de destino.

![Janela Progresso do Studio Visual](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Quando esses processos forem concluídos, você poderá criar uma instância do tipo de cliente do WCF gerado e invocar as operações de serviço.

## <a name="next-steps"></a>Próximas etapas

### <a name="feedback--questions"></a>Perguntas e comentários

Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new). Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Notas de Versão

* Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.
