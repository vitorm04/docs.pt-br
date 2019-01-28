---
title: O .NET Framework e lançamentos fora da banda
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6605809f984a4a1323f555cd73ecb04a67830f46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582052"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>O .NET Framework e lançamentos fora da banda

O .NET Framework está evoluindo para acomodar diferentes plataformas, como o Windows Phone e a Windows Store, bem como a área de trabalho e aplicativos Web tradicionais, e maximizar a reutilização de código. Além de nossas versões regulares do .NET Framework, lançamos também novos recursos fora de faixa (OOB) para melhorar o desenvolvimento interplataforma ou para introduzir novas funcionalidades. Este tópico discute a direção futura do .NET Framework e suas versões OOB.

## <a name="advantages-of-oob-releases"></a>Vantagens das versões OOB
 Enviar novos componentes ou atualizações de componentes fora de faixa permite que Microsoft forneça atualizações mais frequentes para o .NET Framework. Além disso, podemos coletar e responder aos comentários dos clientes de forma mais rápida.

 Quando você usa um recurso OOB em seu aplicativo, os usuários não precisam instalar a versão mais recente do .NET Framework para executar o aplicativo, pois os assemblies OOB são implantados junto com o pacote do aplicativo.

## <a name="how-oob-packages-are-distributed"></a>Como os pacotes OOB são distribuídos
As versões OOB para os componentes principais do CLR (Common Language Runtime) são entregues por meio do [NuGet](https://www.nuget.org/), um gerenciador de pacotes do .NET. O NuGet permite que você procure e adicione bibliotecas facilmente aos seus projetos .NET Framework via Gerenciador de Soluções no Visual Studio. O NuGet faz parte de todas as edições do Visual Studio a partir do Visual Studio 2012. Para verificar se o NuGet está instalado, procure **Gerenciador de Pacotes do NuGet** no menu **Ferramentas** do Visual Studio. Se ele não estiver instalado:

1.  Na barra de menus do Visual Studio, escolha **Ferramentas**, **Extensões e Atualizações** (no Visual Studio 2010, escolha **Gerenciador de Extensões**).

     A caixa de diálogo **Extensões e Atualizações** é aberta.

2.  Escolha **Online**, **Gerenciador de Pacotes NuGet** e, em seguida, escolha **Baixar**.

3.  Após a conclusão do download, reinicie o Visual Studio.

 Para obter instruções de instalação detalhadas, veja [Instalação do NuGet](/nuget/install-nuget-client-tools) no site de Documentação do NuGet. Para saber mais sobre o NuGet, veja a [documentação do NuGet](/nuget).

## <a name="using-a-nuget-oob-package"></a>Usando um pacote OOB do NuGet
 Após instalar o NuGet, você poderá procurar e adicionar referências aos pacotes NuGet usando o Gerenciador de Soluções no Visual Studio:

1.  Abra o menu de atalho para seu projeto no Visual Studio e, em seguida, escolha **Gerenciar Pacotes NuGet**. (Esta opção também está disponível no menu **Projeto**.)

2.  No painel esquerdo, escolha **Online**.

3.  Se você deseja usar pacotes de pré-lançamento, na caixa de lista suspensa no painel intermediário, escolha **Incluir Pré-lançamento** em vez de **Somente Estável**.

4.  No painel direito, use a caixa **Pesquisar** para localizar o pacote que deseja usar. Alguns pacotes da Microsoft são identificados pelo logotipo do Microsoft .NET Framework. Todos eles identificam Microsoft como o editor.

 ![Gerenciador de pacotes NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")

 Conforme mencionado anteriormente, quando você implanta um aplicativo que usa um pacote OOB, os assemblies OOB são fornecidos com o pacote do aplicativo.

## <a name="types-of-oob-releases"></a>Tipos de versão OOB
 Normalmente, um conjunto OOB possui uma ou várias versões de pré-lançamento e uma versão estável. A licença que acompanha uma versão pré-lançamento normalmente não permite a redistribuição, mas permite que você teste um pacote e forneça comentários. Os comentários são incorporados em quaisquer atualizações feitas no pacote. Um versão final é distribuída na forma de pacote estável com o NuGet e inclui uma licença que permite redistribuir o pacote Nuget com seu aplicativo. Pacotes estáveis têm suprote pela Microsoft. A Microsoft fornece suporte para IntelliSense, bem como para outros tipos de documentação, como postagens em blogs e respostas em fóruns para todos os pacotes. Além disso, o código-fonte pode ser disponibilizado em alguns pacotes, mas não em todos. Para consultar anúncios em relação a novos pacotes e atualizações, inscreva-se no [Blog do .NET Framework](https://blogs.msdn.com/b/dotnet/).

 Para encontrar pré-lançamentos e pacotes estáveis, selecione **Incluir Pré-lançamento** no Gerenciador de pacotes NuGet.

 Para receber notificações sobre lançamentos de pacotes estáveis, assine o [feed do .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

## <a name="see-also"></a>Consulte também

- [Introdução](../../../docs/framework/get-started/index.md)