---
title: Diretrizes da biblioteca .NET de software livre
description: Práticas recomendadas para que os desenvolvedores criem bibliotecas .NET de alta qualidade.
ms.date: 10/17/2018
ms.openlocfilehash: c1e1c302eede86fd5555a8e84630e216e96f1ce7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706446"
---
# <a name="open-source-library-guidance"></a>Diretrizes da biblioteca de software livre

Estas diretrizes fornecem recomendações para que os desenvolvedores criem bibliotecas .NET de alta qualidade. Esta documentação concentra-se no *quê* e no *porquê* ao criar uma biblioteca .NET, não no *como*.

Aspectos das bibliotecas .NET de software livre de alta qualidade:

> [!div class="checklist"]
>
> * **Inclusivas** – as bibliotecas .NET de qualidade se esforçam para dar suporte a várias plataformas, linguagens de programação e aplicativos.
> * **Estáveis** – as bibliotecas .NET de qualidade coexistem no ecossistema do .NET, em execução em aplicativos criados com várias bibliotecas.
> * **Projetadas para evoluir** – as bibliotecas .NET devem melhorar e evoluir ao longo do tempo, continuando a dar suporte aos usuários existentes.
> * **Depuráveis** – as bibliotecas .NET devem usar as ferramentas mais recentes para criar uma ótima experiência de depuração para os usuários.
> * **Confiáveis** – as bibliotecas .NET têm a confiança dos desenvolvedores por publicarem no NuGet usando práticas recomendadas de segurança.

> [!div class="nextstepaction"]
> [Introdução](./get-started.md)

## <a name="types-of-recommendations"></a>Tipos de recomendações

Cada artigo apresenta quatro tipos de recomendação: **Fazer**, **Considerar**, **Evitar** e **Não fazer**. O tipo de recomendação indica a intensidade em que ela deve ser seguida.

Procure quase sempre seguir a recomendação **Fazer**. Por exemplo:

**✔️ FAZER** a distribuição de sua biblioteca usando um pacote NuGet.

Por outro lado, as recomendações **Considerar** geralmente devem ser seguidas, mas há exceções à regra legítimas e você não precisará se preocupar caso não possa seguir as diretrizes:

**✔️ CONSIDERAR** o uso do [SemVer 2.0.0](https://semver.org/) para criar a versão do seu pacote NuGet.

As recomendações **Evitar** mencionam coisas que em geral não são ideais, mas há casos em que, às vezes, quebrar a regra faz sentido:

**❌ evitar** As referências do pacote NuGet que exigem uma versão exata.

Por fim, as recomendações **Não fazer** indicam algo que você quase nunca deve fazer:

**❌ não** publique versões de nome forte e não forte da sua biblioteca. Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Avançar](get-started.md)
