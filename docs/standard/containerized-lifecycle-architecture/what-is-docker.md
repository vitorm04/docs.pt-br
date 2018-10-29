---
title: O que é o Docker?
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 056fb613c078cc407380060dc11890406ac8cffd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197672"
---
# <a name="what-is-docker"></a>O que é o Docker?

[Docker](https://www.docker.com/) é um [projeto de código-fonte aberto](https://github.com/docker/docker) para automatizar a implantação de aplicativos como contêineres autossuficientes portáteis que podem ser executados na nuvem ou local (veja a Figura 1 - 2). O docker é também uma [empresa](https://www.docker.com/) que promove e desenvolve dessa tecnologia, trabalhando em colaboração com fornecedores do Windows, incluindo a Microsoft e de nuvem, o Linux.

![](./media/image2.png)

Figura 1-2-Docker implanta contêineres em todas as camadas da nuvem híbrida

Os contêineres de imagem do Docker podem ser executados nativamente no Linux e no Windows. No entanto, imagens do Windows podem executar somente em hosts do Windows e imagens do Linux podem ser executado apenas em hosts do Linux, que significa que um servidor de host ou em uma VM.

Os desenvolvedores podem usar ambientes de desenvolvimento no Windows, Linux ou macOS. No computador de desenvolvimento, o desenvolvedor é executado de um host do Docker para o qual Docker imagens forem implantadas, incluindo o aplicativo e suas dependências. Os desenvolvedores que trabalham no Linux ou no Mac usam um host do Docker que é baseado no Linux, e eles podem criar imagens apenas para contêineres do Linux. (Os desenvolvedores que trabalham no Mac podem editar o código ou executar a interface de linha de comando do Docker \[CLI\] do macOS, mas, até o presente momento, os contêineres não são executados diretamente no macOS.) Desenvolvedores que trabalham no Windows podem criar imagens para contêineres do Linux ou do Windows.

Para hospedar contêineres em ambientes de desenvolvimento e fornecer ferramentas para desenvolvedores adicionais, o Docker envia o [Docker Community Edition (CE)](https://www.docker.com/community-edition) para Windows ou para o macOS. Esses produtos instalam a VM necessária (o host do Docker) para hospedar os contêineres. O Docker também disponibiliza o [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), que foi projetado para desenvolvimento empresarial e é usado por equipes de TI que criam, enviam e executam aplicativos de grande porte críticos para os negócios em produção.

Para executar [contêineres do Windows](/virtualization/windowscontainers/about/), há dois tipos de tempos de execução:

-   **Contêiner do Windows Server** esse tempo de execução fornece isolamento de aplicativo por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres em execução no host.

-   **Contêiner do Hyper-V** isso expande o isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma VM altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com os contêineres do Hyper-V, fornecendo melhor isolamento.

As imagens para esses contêineres são criadas da mesma forma e funcionam da mesma. A diferença está em como o contêiner é criado a partir da imagem — executar um contêiner do Hyper-V exige um parâmetro extra. Para obter detalhes, consulte [Contêineres do Hyper-V](/virtualization/windowscontainers/about/).

## <a name="comparing-docker-containers-with-vms"></a>Comparando contêineres do Docker com máquinas virtuais

Figura 1 a 3 mostra uma comparação entre VMs e Docker contêineres.

Como os contêineres requerem muito menos recursos (por exemplo, eles não é necessário um sistema operacional completo), eles são fáceis de implantar e iniciarem rapidamente por eles. Isso torna possível que você tenha maior densidade, o que significa que você pode executar mais serviços na mesma unidade de hardware, reduzindo os custos.

Como um efeito colateral da execução no mesmo kernel, você deve obter menos isolamento que as VMs.

A meta principal de uma imagem é que ela torne o ambiente (dependências) o mesmo entre diferentes implantações. Isso significa que é possível depurá-la em seu computador e, em seguida, implantá-la em outro computador com o mesmo ambiente garantido.

Uma imagem de contêiner é uma maneira de empacotar um aplicativo ou serviço e implantá-lo de maneira confiável e reproduzível. Nesse sentido, o Docker não é apenas uma tecnologia, também é uma filosofia e um processo.

Ao usar o Docker, você não verá os desenvolvedores dizem, "Funciona no meu computador, por que não em produção?" Eles podem simplesmente dizer: "É executado no Docker," porque o aplicativo empacotado do Docker pode ser executado em qualquer ambiente do Docker com suporte, e ela será executada da maneira que ele se destinava a em todos os destinos de implantação (desenvolvimento, QA, preparo, produção, etc.).

![](./media/image3.png)

Figura 1 a 3: comparação das VMs tradicionais para contêineres do Docker


>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](docker-terminology.md)
