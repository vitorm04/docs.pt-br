---
title: "O que é o Docker?"
description: "Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c75b2fa87e5aad93693c76c3bbd135044b36525f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="what-is-docker"></a>O que é o Docker?

[Docker](https://www.docker.com/) é um [projeto de código-fonte aberto](https://github.com/docker/docker) para automatizar a implantação de aplicativos como contêineres auto-suficiente, portáteis que podem ser executados na nuvem ou local (consulte a Figura 1 e 2). A docker é também um [empresa](https://www.docker.com/) que promove e desenvolve essa tecnologia, trabalhar em colaboração com a nuvem, Linux e fornecedores do Windows, incluindo Microsoft.

![](./media/image2.png)

Figura 1-2-Docker implanta contêineres em todas as camadas da nuvem híbrida

Contêineres de imagem do docker podem executar nativamente no Linux e Windows. No entanto, imagens do Windows podem executar somente em hosts do Windows e Linux imagens podem executar somente em hosts Linux, que significa que um servidor de host ou em uma VM.

Os desenvolvedores podem usar os ambientes de desenvolvimento no Windows, Linux ou macOS. No computador de desenvolvimento, o desenvolvedor executa um host Docker para qual Docker imagens forem implantadas, incluindo o aplicativo e suas dependências. Os desenvolvedores que trabalham no Linux ou no Mac usam um host Docker é baseado em Linux, e podem criar imagens apenas para contêineres do Linux. (Os desenvolvedores que trabalham no Mac podem editar o código ou executar a interface de linha de comando do Docker \[CLI\] de macOS, mas, redação deste artigo, os contêineres não executados diretamente em macOS.) Os desenvolvedores que trabalham no Windows podem criar imagens de contêineres do Windows ou Linux.

Para hospedar os contêineres em ambientes de desenvolvimento e fornecem ferramentas de desenvolvedor adicionais, vem Docker [Docker Community Edition (CE)](https://www.docker.com/community-edition) para Windows ou macOS. Esses produtos instalam o VM necessário (o host do Docker) para hospedar os contêineres. Docker também disponibiliza [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), que é projetado para desenvolvimento empresarial e é usado por equipes de TI que criam, enviar e executar aplicativos essenciais aos negócios grandes em produção.

Para executar [contêineres do Windows](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), há dois tipos de tempos de execução:

-   **Contêiner do Windows Server** esse tempo de execução fornece isolamento de aplicativos por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres em execução no host.

-   **Contêiner do Hyper-V** isso expande o isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma máquina virtual altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com os contêineres do Hyper-V, fornece melhor isolamento.

As imagens para esses contêineres são criadas da mesma forma e funcionam da mesma. A diferença é como o contêiner é criado por meio da imagem, a execução de um contêiner do Hyper-V exige um parâmetro extra. Para obter detalhes, consulte [contêineres do Hyper-V](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Comparando os contêineres do Docker com máquinas virtuais

Figura 1-3 mostra uma comparação entre VMs e Docker contêineres.

Como contêineres exigem muito menos recursos (por exemplo, eles não é necessário um SO completo), são fáceis de implantar e começar rapidamente. Isso possibilita que você tenha a densidade mais alta, o que significa que você pode executar mais serviços na mesma unidade de hardware, reduzindo os custos.

Como um efeito colateral da execução no mesmo kernel, você obtém menos isolamento de máquinas virtuais.

O objetivo principal de uma imagem é que ele faz o ambiente (dependências) os mesmos entre diferentes implantações. Isso significa que você pode depurá-lo em seu computador e, em seguida, implantá-lo para outro computador com o mesmo ambiente de garantia.

Uma imagem de contêiner é uma maneira para empacotar um aplicativo ou serviço e implantá-lo de uma maneira confiável e reproduzível. Nesse sentido, o Docker não é apenas uma tecnologia, também é uma filosofia e um processo.

Ao usar o Docker, você não verá os desenvolvedores dizer, "Funciona no meu computador, por que não em produção?" Pode simplesmente dizem, "Executa no Docker," porque o aplicativo empacotado do Docker pode ser executado em qualquer ambiente de Docker, e ela será executada da maneira que ele estivesse destinado a em todos os destinos de implantação (desenvolvimento, QA, preparo, produção, etc.).

![](./media/image3.png)

Figura 1-3: comparação das VMs tradicionais para contêineres do Docker


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (docker-terminology.md)
