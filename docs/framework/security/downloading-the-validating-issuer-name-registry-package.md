---
title: Baixando o Pacote de Registro do nome do emissor de validação
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940576"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>Baixe o pacote de registro de nome de emissor validação

Este tópico descreve como baixar e usar o VINR (Registro do Nome do Emissor de Validação) no projeto.

O VINR está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto. Se você ainda não tiver o NuGet instalado, acesse [nuget.org](https://nuget.org) para instalá-lo. Você pode ver o histórico de controle de versão para a extensão visitando sua página no NuGet: [Validando o registro de nome de emissor do Microsoft](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>Usar a GUI do Gerenciador de pacotes

1. No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.

2. Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `ValidatingIssuerNameRegistry` e pressione **Enter**.

3. No painel de resultados, clique no botão **Instalar** do primeiro resultado.

4. O download do pacote será iniciado. Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida. Se concordar com os termos de licença, clique em **Eu Aceito**.

5. Os últimos assemblies do VINR serão baixados e adicionados ao projeto.

## <a name="use-the-package-manager-console"></a>Use o Console do Gerenciador de pacotes

1. No Visual Studio, clique em **ferramentas** > **Gerenciador de pacotes NuGet** > **Package Manager Console**.

2. O **Console do Gerenciador de Pacotes** será exibido. Insira o seguinte texto e pressione **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. Os últimos assemblies do VINR serão baixados e adicionados ao projeto.