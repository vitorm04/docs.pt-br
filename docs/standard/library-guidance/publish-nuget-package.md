---
title: Publicar um pacote NuGet
description: Práticas recomendadas para a publicação bibliotecas .NET NuGet.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369677"
---
# <a name="publishing-a-nuget-package"></a>Publicar um pacote NuGet

Pacotes do NuGet são publicados e consumidos de repositórios de pacote. Enquanto o NuGet.org é a mais amplamente conhecido e usado de repositório, há muitos lugares para publicar pacotes do NuGet:

* **[NuGet.org](https://www.nuget.org/)**  é o principal repositório online para pacotes do NuGet. Todos os pacotes em NuGet.org estão publicamente disponíveis para todos. Por padrão, o Visual Studio tem NuGet.org como uma origem de pacote e para muitos desenvolvedores NuGet.org é o repositório de pacote somente com que eles poderá interagir. NuGet.org é o melhor lugar para publicar pacotes estáveis e pacotes de pré-lançamento que você deseja comentários da comunidade no.

* **[MyGet](https://myget.org/)**  dá suporte ao serviço de repositório [feeds de pacote personalizado gratuito para projetos de código-fonte aberto](https://www.myget.org/opensource). Um feed personalizado do MyGet público é um lugar ideal para publicar pacotes de pré-lançamento criados pelo seu serviço de CI. MyGet também fornece feeds privados comercialmente.

* Um **[feed local](/nuget/hosting-packages/local-feeds)** permite que você trate uma pasta como um repositório de pacotes e torna o `*.nupkg` arquivos na pasta acessível pelo NuGet. Um feed local é útil para testar um pacote do NuGet antes de publicá-lo em NuGet.org.

> [!NOTE]
> NuGet.org [não permite que um pacote a ser excluído](/nuget/policies/deleting-packages) depois que ele é carregado. Um pacote pode ser removido da lista para que não é publicamente visível na interface do usuário, mas o `*.nupkg` ainda pode ser baixado na restauração. Além disso, o nuget.org não permite a versões de pacote duplicado. Para corrigir um pacote do NuGet com um erro que você precise remover o pacote incorreto da lista, aumente o número de versão e publicar uma nova versão do pacote.

**FAZER ✔️** [publicar pacotes estáveis e pacotes de pré-lançamento](/nuget/create-packages/publish-a-package) desejar comentários da comunidade do logon no NuGet.org.

**Considere a possibilidade de ✔️** publicar pacotes de pré-lançamento para uma MyGet feed de um build de integração contínua.

**Considere a possibilidade de ✔️** testar pacotes no ambiente de desenvolvimento usando um feed local ou MyGet. Verifique o pacote funciona em seguida, publique-o em NuGet.org.

## <a name="nugetorg-security"></a>Segurança de NuGet.org

É importante que os atores ruins não é possível acessar sua conta do NuGet e carregar uma versão mal-intencionado da sua biblioteca. NuGet.org oferece dois fatores autenticação e notificações por email quando um pacote é publicado. Habilitar esses recursos após fazer logon no NuGet.org sobre o **configurações de conta** página.

![texto ALT](./media/publish-nuget-package/nuget-2fa.png "NuGet segurança da conta")

**FAZER ✔️** usa uma conta da Microsoft para entrar NuGet.

**FAZER ✔️** habilitar a autenticação de dois fatores para acessar o NuGet.

**FAZER ✔️** habilitar notificação por email quando um pacote é publicado.

>[!div class="step-by-step"]
[Anterior](./sourcelink.md)
[Próximo](./versioning.md)
