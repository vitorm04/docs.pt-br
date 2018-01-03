---
title: Baixando o Pacote do Manipulador de Token da Web JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5982830404d8d8780bf41153741928b68dc5c7d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a>Baixando o Pacote do Manipulador de Token da Web JSON
Este tópico descreve como baixar e usar o Manipulador de Token Web JSON no projeto.  
  
## <a name="downloading-the-json-web-token-handler"></a>Baixando o Manipulador de Token da Web JSON  
 A extensão Manipulador de Token Web JSON está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto. Se você ainda não tiver o NuGet instalado, acesse [nuget.org](http://nuget.org) para instalá-lo. Veja o histórico de controle de versão da extensão visitando sua página no NuGet: [Manipulador de Token Web JSON no NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a>Baixando o Manipulador de Token Web JSON usando a GUI do Gerenciador de Pacotes  
  
1.  No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.  
  
2.  Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `JWT Token Handler` e pressione **Enter**.  
  
3.  No painel de resultados, clique no botão **Instalar** do primeiro resultado.  
  
4.  O download do pacote será iniciado. Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida. Se concordar com os termos de licença, clique em **Eu Aceito**.  
  
5.  Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a>Baixando o Manipulador de Token Web JSON usando o Console do Gerenciador de Pacotes  
  
1.  No Visual Studio, clique em **Ferramentas**, **Gerenciador de Pacotes da Biblioteca** e, em seguida, em **Console do Gerenciador de Pacotes**.  
  
2.  O **Console do Gerenciador de Pacotes** será exibido. Insira o seguinte texto e pressione **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.
