---
title: "Baixando o Pacote de Registro do nome do emissor de validação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>Baixando o Pacote de Registro do nome do emissor de validação
Este tópico descreve como baixar e usar o VINR (Registro do Nome do Emissor de Validação) no projeto.  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>Baixando o Registro do Nome do Emissor de Validação  
 O VINR está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto. Se você ainda não tiver o NuGet instalado, acesse [nuget.org](http://nuget.org) para instalá-lo. Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Registro do Nome do Emissor de Validação do Microsoft no NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>Baixando o Registro do Nome do Emissor de Validação usando a GUI do Gerenciador de Pacotes  
  
1.  No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.  
  
2.  Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `ValidatingIssuerNameRegistry` e pressione **Enter**.  
  
3.  No painel de resultados, clique no botão **Instalar** do primeiro resultado.  
  
4.  O download do pacote será iniciado. Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida. Se concordar com os termos de licença, clique em **Eu Aceito**.  
  
5.  Os últimos assemblies do VINR serão baixados e adicionados ao projeto.  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>Baixando o Registro do Nome do Emissor de Validação usando o Console do Gerenciador de Pacotes  
  
1.  No Visual Studio, clique em **Ferramentas**, **Gerenciador de Pacotes da Biblioteca** e, em seguida, em **Console do Gerenciador de Pacotes**.  
  
2.  O **Console do Gerenciador de Pacotes** será exibido. Insira o seguinte texto e pressione **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  Os últimos assemblies do VINR serão baixados e adicionados ao projeto.
