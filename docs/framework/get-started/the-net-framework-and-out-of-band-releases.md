---
title: .NET Framework e lançamentos fora da banda
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181576"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework e lançamentos fora da banda

O .NET Framework evoluiu para acomodar diferentes plataformas, como aplicativos UWP e aplicativos tradicionais de desktop e web, e para maximizar a reutilização de códigos. Além das versões regulares do .NET Framework, novos recursos são lançados fora da banda (OOB) para melhorar o desenvolvimento entre plataformas ou para introduzir novas funcionalidades.

## <a name="advantages-of-oob-releases"></a>Vantagens das versões OOB

O envio de novos componentes ou atualizações para componentes fora da banda permite que a Microsoft forneça atualizações mais freqüentes ao .NET Framework. Além disso, podemos coletar e responder aos comentários dos clientes de forma mais rápida.

Quando você usa um recurso OOB em seu aplicativo, seus usuários não têm que instalar a versão mais recente do .NET Framework para executar seu aplicativo, porque os conjuntos OOB são implantados com o pacote do aplicativo.

## <a name="how-oob-packages-are-distributed"></a>Como os pacotes OOB são distribuídos

As versões oOB para componentes CLR (Core Common Language Runtime, tempo de execução de linguagem comum) são entregues através do [NuGet](https://www.nuget.org/), que é o gerenciador de pacotes para .NET. O NuGet permite que você navegue e adicione bibliotecas aos seus projetos .NET Framework facilmente de dentro do Visual Studio. NuGet Package Manager está incluído em todas as edições do Visual Studio começando com visual studio 2012. Procure o **NuGet Package Manager** no menu **Ferramentas** no Visual Studio. Se não estiver instalado, siga as instruções sobre [como instalar nuget](/nuget/install-nuget-client-tools). Para obter mais informações sobre o NuGet, consulte os [docs nuget](/nuget).

## <a name="use-a-nuget-oob-package"></a>Use um pacote NuGet OOB

Se o NuGet Package Manager estiver instalado, você pode navegar e adicionar referências aos pacotes NuGet usando o Solution Explorer no Visual Studio:

1. Abra o menu de atalho para seu projeto no Visual Studio e, em seguida, escolha **Gerenciar Pacotes NuGet**. (Esta opção também está disponível no menu **Projeto**.)

2. No painel esquerdo, escolha **Online**.

3. Se você deseja usar pacotes de pré-lançamento, na caixa de lista suspensa no painel intermediário, escolha **Incluir Pré-lançamento** em vez de **Somente Estável**.

4. No painel direito, use a caixa **Pesquisar** para localizar o pacote que deseja usar. Alguns pacotes da Microsoft são identificados pelo logotipo do Microsoft .NET Framework. Todos eles identificam Microsoft como o editor.

![O gerenciador de pacotes NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Conforme mencionado anteriormente, quando você implanta um aplicativo que usa um pacote OOB, os assemblies OOB são fornecidos com o pacote do aplicativo.

## <a name="types-of-oob-releases"></a>Tipos de versão OOB

Normalmente, um conjunto OOB possui uma ou várias versões de pré-lançamento e uma versão estável. A licença que acompanha uma versão pré-lançamento normalmente não permite a redistribuição, mas permite que você teste um pacote e forneça comentários. Os comentários são incorporados em quaisquer atualizações feitas no pacote. Um versão final é distribuída na forma de pacote estável com o NuGet e inclui uma licença que permite redistribuir o pacote Nuget com seu aplicativo. Pacotes estáveis têm suprote pela Microsoft. A Microsoft fornece suporte para IntelliSense, bem como para outros tipos de documentação, como postagens em blogs e respostas em fóruns para todos os pacotes. Além disso, o código-fonte pode ser disponibilizado em alguns pacotes, mas não em todos. Para consultar anúncios em relação a novos pacotes e atualizações, inscreva-se no [Blog do .NET Framework](https://devblogs.microsoft.com/dotnet/).

Para encontrar pacotes pré-lançamento e estável, escolha **Incluir pré-lançamento** no NuGet Package Manager.

## <a name="see-also"></a>Confira também

- [Começando](index.md)
