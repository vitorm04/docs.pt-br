---
title: Implantar aplicativos .NET existentes como contêineres do Windows
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Implantar aplicativos .NET existentes como contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 829f33aba14d79d7d9003d1ac7472a19060d401a
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Implantar aplicativos .NET existentes como contêineres do Windows

Implantações baseadas em contêineres do Windows são aplicáveis a aplicativos com otimização de nuvem e aplicativos de nuvem nativo.

No entanto, neste guia e especialmente nas seções a seguir, principalmente concentra-se sobre o uso de contêineres do Windows para *otimizada para a nuvem* aplicativos onde você não precisa Refaça a arquitetura de seu aplicativo.

## <a name="what-are-containers-linux-or-windows"></a>O que são contêineres? (Linux ou Windows)

Contêineres são uma maneira para empacotar um aplicativo em seu próprio pacote isolado. Em seu contêiner, o aplicativo não é afetado por aplicativos ou processos que existem fora do contêiner. Tudo o que o aplicativo depende a executar com êxito como um processo está dentro do contêiner. Sempre que o contêiner pode mover, os requisitos do aplicativo serão sempre atendidos, em termos de dependências diretas, pois ele é fornecido com tudo o que precisa ser executado (biblioteca de dependências, tempos de execução e assim por diante).

A principal característica de um contêiner é tornar o ambiente iguais entre diferentes implantações como o contêiner em si é fornecido com todas as dependências necessárias. Você pode depurar o aplicativo em seu computador e, em seguida, implantá-la em outra máquina, com o mesmo ambiente de garantia.

Um contêiner é uma instância de uma imagem de contêiner. Uma imagem de contêiner é uma maneira de um aplicativo ou serviço (como um instantâneo) do pacote e, em seguida, implantá-lo de forma confiável e reproduzível. Você poderia dizer que o Docker não é que somente uma tecnologia-it também uma filosofia e um processo.

Como contêineres diariamente se tornam mais comuns, eles estão se tornando um todo o setor "unidade de implantação".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Benefícios de contêineres (mecanismo de Docker no Linux ou Windows)

Criação de aplicativos usando contêineres, que também pode ser definida como blocos de construção leve-oferece um aumento significativo na agilidade para criação, envio e execução de qualquer aplicativo, em qualquer infraestrutura.

Com os contêineres, você pode colocar qualquer aplicativo de desenvolvimento para produção com pouca ou nenhuma alteração de código, graças a integração de Docker em nuvem, sistemas operacionais e ferramentas de desenvolvedor da Microsoft.

Quando você implantar VMs sem formatação, você provavelmente já tem um método em vigor para a implantação de aplicativos do ASP.NET para suas VMs. No entanto, é provável, que o método envolve várias etapas manuais ou automatizados de processos complexos usando uma ferramenta de implantação como Puppet ou uma ferramenta semelhante. Talvez seja necessário executar tarefas como modificar itens de configuração, copiando o conteúdo entre servidores de aplicativos e programas de instalação interativa com base em configurações do. msi, seguidas por teste em execução. Todas essas etapas na implantação adicionam tempo e o risco em implantações. Você obterá falhas sempre que uma dependência não está presente no ambiente de destino.

Em contêineres do Windows, o processo de empacotamento de aplicativos é totalmente automatizado. Contêineres do Windows é baseado na plataforma de Docker, que oferece as atualizações automáticas e reversões para implantações de contêiner. A principal melhoria obtida usando o mecanismo do Docker é que você crie imagens, que são como os instantâneos do seu aplicativo, com todas as suas dependências. As imagens são imagens do Docker (uma contêiner imagem do Windows, neste caso). As imagens de executam aplicativos do ASP.NET em contêineres, sem voltar ao código-fonte. O instantâneo de contêiner torna-se a unidade de implantação.

Muitas organizações estão containerizing aplicativos monolíticos existentes pelos seguintes motivos:

-   **Versão agilidade por meio de implantação melhor**. Contêineres oferecem um contrato de implantação consistente entre o desenvolvimento e operações. Quando você usar contêineres, você não ouvirá desenvolvedores dizer, "Funciona no meu computador, por que não em produção?" Pode dizer, "Ele é executado como um contêiner, ele será executado em produção." O aplicativo empacotado, com todas as suas dependências, pode ser executado em qualquer ambiente contêiner com suporte. Ela será executada da maneira que ele deve ser executado em todos os destinos de implantação (desenvolvimento, QA, preparo, produção). Contêineres de eliminam frictions mais quando eles se movem de um estágio para o próximo, o que melhora significativamente a implantação, e você pode enviar mais rápido.

-   **Reduções de custos**. Contêineres de levam a reduzir custos, passando a consolidação e a remoção do hardware existente ou de aplicativos em execução em uma densidade mais alta por unidade de hardware.

-   **Portabilidade**. Contêineres são modular e portátil. Contêineres do docker têm suporte em qualquer sistema operacional (Linux e Windows), em qualquer nuvem pública principais (Microsoft Azure, AWS Amazon, Google, IBM) e no local e privada ou ambientes de nuvem híbrida.

-   **Controle**. Contêineres oferecem um ambiente flexível e seguro que é controlado no nível do contêiner. Um contêiner pode ser protegido, isolado e até mesmo limitado, definindo políticas de restrição de execução no contêiner. Conforme detalhado na seção sobre contêineres do Windows, contêineres do Hyper-V e Windows Server 2016 oferecem opções de suporte da empresa adicionais.

Melhorias significativas no controle, portabilidade e agilidade gerar reduções de custos significativas, por fim, quando você usar contêineres para desenvolver e manter aplicativos.

## <a name="what-is-docker"></a>O que é o Docker?

[Docker](https://www.docker.com/) é um [projeto de código-fonte aberto](https://github.com/docker/docker) que automatiza a implantação de aplicativos como contêineres auto-suficiente, portáteis que podem ser executados na nuvem ou local. O Docker é também um [empresa](https://www.docker.com/) que promove e evolui essa tecnologia. A empresa funciona em colaboração com a nuvem, Linux e fornecedores do Windows, incluindo Microsoft.

![](./media/image6.png)

> **Figura 4 a 6.** O Docker implanta contêineres em todas as camadas da nuvem híbrida

A outra familiarizado com máquinas virtuais, contêineres podem parecer ser bastante semelhante. Um contêiner executa um sistema operacional, tem um sistema de arquivos e pode ser acessado por meio de uma rede, assim como um sistema de computador físico ou virtual. No entanto, a tecnologia e os conceitos por trás de contêineres são muito diferentes das máquinas virtuais. Do ponto de vista do desenvolvedor, um contêiner deve ser tratado mais como um único processo. Na verdade, um contêiner tem um único ponto de entrada para um processo.

Contêineres do docker (para manter a simplicidade, *contêineres*) podem ser executados de modo nativo em Linux e Windows. Durante a execução normais contêineres, contêineres do Windows podem executar somente em hosts do Windows (um servidor de host ou uma máquina virtual) e contêineres do Linux podem executar apenas em hosts Linux. No entanto, em versões recentes do Windows Server e Hyper-V contêineres, um contêiner de Linux também pode executar nativamente no Windows Server usando a tecnologia de isolamento do Hyper-V que atualmente está disponível apenas em contêineres do Windows Server.

Em breve, ambientes mistos com contêineres do Linux e Windows será possível e até mesmo comuns.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Benefícios de contêineres do Windows para seus aplicativos existentes do .NET

Os benefícios do uso de contêineres do Windows são basicamente os mesmos benefícios que você obtém de contêineres, em geral. Usar contêineres do Windows é sobre melhorando a agilidade, a mobilidade e o controle.

Consultem os aplicativos existentes do .NET para os aplicativos que foram criados usando o .NET Framework. Por exemplo, eles podem ser aplicativos ASP.NET tradicionais-eles não usam o .NET Core, que é mais recente e executa várias plataformas no Linux, Windows e MacOS.

A dependência principal no .NET Framework é Windows. Ele também tem dependências secundárias, como IIS e System. Web no ASP.NET tradicional.

Um aplicativo do .NET Framework deve ser executados no Windows, período. Se você deseja coloca os aplicativos existentes do .NET Framework e não pode ou não quiser investir em uma migração para o .NET Core ("se ele está funcionando corretamente, não migrá-lo"), a única opção que você tem para contêineres é usar contêineres do Windows.

Portanto, um dos principais benefícios dos contêineres do Windows é que eles oferecem uma maneira de modernizar seus aplicativos existentes do .NET Framework que estão em execução no enormemente por meio do Windows. Por fim, contêineres do Windows obtém os benefícios que você está procurando usando contêineres agilidade, portabilidade e maior controle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Escolha um sistema operacional de destino com. Contêineres baseados em rede

Dada a diversidade de sistemas operacionais que são suportados pelo Docker, bem como as diferenças entre o .NET Framework e o .NET Core, você deve ter como destino um sistema operacional específico e versões específicas com base na estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows fornecem características diferentes (como o IIS em vez de um servidor web auto-hospedado como Kestrel) que podem ser necessários para aplicativos do .NET Framework ou no .NET Core.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Figura 4-7 mostra as versões do sistema operacional que você pode direcionar, dependendo da versão do aplicativo do .NET Framework.

![](./media/image7.png)

> **Figura 4-7.** Sistemas operacionais com base na versão do .NET Framework de destino

Em cenários de migração para aplicativos existentes ou herdados que são baseados em aplicativos do .NET Framework, as dependências principais são no Windows e no IIS. Sua única opção é usar imagens do Docker com base no Windows Server Core e o .NET Framework.

Quando você adiciona o nome da imagem ao seu arquivo de Dockerfile, você pode selecionar o sistema operacional e versão por meio de uma marca, como nos exemplos a seguir para imagens de contêiner do Windows com base em .NET Framework:

> | **Marca** | **Versão e sistema** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4. x no Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4. x com personalização adicional do ASP.NET, no Windows Server Core |

.NET Core (plataforma cruzada para Linux e Windows), as marcas seria semelhante ao seguinte:

> | **Marca** | **Versão e sistema**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | Núcleo do .NET 2.0 somente em tempo de execução no Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Núcleo do .NET 2.0 somente em tempo de execução no Windows Nano Server |

### <a name="multi-arch-images"></a>Arch várias imagens

Começando em meados de 2017, você também pode usar um novo recurso no Docker chamado [multi-arch](https://github.com/moby/moby/issues/15866) imagens. Imagens do Docker de núcleo do .NET podem usar vários arch marcas. O Dockerfile arquivos não precisa definir o sistema operacional de destino. O recurso de vários arch permite uma única marca a ser usado em várias configurações de máquina. Por exemplo, com vários arch, você pode usar uma marca comuns: **microsoft/dotnet:2.0.0-runtime**. Se você puxar essa marca de um ambiente de contêiner do Linux, você receberá a imagem baseada em Debian. Se você receber essa marca de um ambiente de contêiner do Windows, você pode obter a imagem baseada em Nano Server.

Para as imagens do .NET Framework, como o tradicional do .NET Framework oferece suporte a somente o Windows, você não pode usar o recurso de vários arch.

## <a name="windows-container-types"></a>Tipos de contêineres do Windows

Como contêineres do Linux, contêineres do Windows Server são gerenciados usando o mecanismo do Docker. Ao contrário de contêineres do Linux, contêineres do Windows incluem dois tipos diferentes de contêiner ou executam contêineres vezes-Windows Server e o isolamento do Hyper-V.

**Contêineres do Windows Server**: fornece isolamento de aplicativos por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres que estão em execução no host. Esses contêineres não fornecem um limite de segurança hostil e não devem ser usados para isolar o código não confiável. Devido a espaço de kernel compartilhado, esses contêineres exigem a mesma versão do kernel e a configuração.

**Isolamento do Hyper-V**: expande o isolamento fornecido pelos contêineres do Windows Server executando cada contêiner em uma máquina virtual altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com outros contêineres no mesmo host. Esses contêineres são projetados para hostil multilocatário de host, com a mesma garantia de segurança de uma VM. Como esses contêineres não compartilham o kernel com o host ou outros contêineres no host, eles podem executar kernels com diferentes versões e as configurações (com as versões com suporte). Por exemplo, todos os contêineres do Windows no Windows 10 usam o isolamento do Hyper-V para utilizar a versão de kernel do Windows Server e a configuração.

Executar um contêiner no Windows, com ou sem isolamento do Hyper-V é uma decisão de tempo de execução. Você pode optar por criar o contêiner com o isolamento do Hyper-V inicialmente e, em tempo de execução, escolha para executá-lo como um contêiner do Windows Server.

### <a name="additional-resources"></a>Recursos adicionais

-   **Documentação de contêineres do Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Conceitos básicos de contêineres do Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **Infográfico: Microsoft e contêineres**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)


## <a name="the-container-ecosystem-in-azure"></a>O ecossistema de contêineres no Azure

Nas seções anteriores, ele tem sido explicado quais são os benefícios de contêineres do Docker, bem como obter detalhes sobre as imagens de contêiner específico para aplicativos .NET. Obter informações genéricas tudo o que são fundamentais para desenvolver ou coloca um aplicativo.
No entanto, ao pensar sobre o ambiente de implantação de produção ou até mesmo ambientes de controle de qualidade e desenvolvimento/teste, o Microsoft Azure fornece uma aberta e ampla variedade de opções, um ecossistema de contêiner completa na nuvem (mostrado no diagrama abaixo). Dependendo das necessidades do seu aplicativo específico, você deve escolher um ou outro produto do Azure.

![](./media/image7.5.png)

> **Figura 4-7.5.** O ecossistema de contêineres no Azure

Do ecossistema de contêiner no Azure, os seguintes produtos de contêineres que são considerados a infraestrutura de suporte:
-   **Instâncias de contêiner do Azure (ACI)**
-   **Máquinas virtuais do Azure** (com suporte do contêiner)
-   **Conjuntos de escala de máquinas virtuais do Azure** (com suporte do contêiner)

Desses três ACI fornece um grande benefício, que é o fato de que você não precisa manter o sistema operacional subjacente, você não precisa para atualização/patch, etc., mas ainda ACI é posicionado no nível de infraestrutura, como melhor explicado nas seções futuras deste livro.

Os produtos em contêineres de suporte do Azure que estão ao mesmo tempo posicionado mais de PaaS (plataforma como serviço) níveis são:

-   **Serviço de Aplicativo do Azure**
-   **Serviço de Kubernetes do Azure (AKS e ACS)**
-   **Malha do serviço do Azure** 
-   **Lote do Azure** 

Em seguida, o registro de contêiner do Azure é um registro de contêiner escalonável alta hospedado no Azure que você pode usar de todos os produtos anteriores ao registrar e implantar suas imagens de contêiner personalizado.

Além disso, seus contêineres, você pode usar outros serviços gerenciados no Azure como o Azure SQL Database, cache Redis do Azure, banco de dados do Azure Cosmos, etc. Além disso, há soluções de terceiros/plataformas disponíveis no Azure Marketplace como nuvem Foundry e OpenShift onde você também pode usar contêineres no Azure. 

Nas próximas seções, você pode explorar as recomendações da Microsoft sobre quando usar cada um desses produtos do Azure e soluções especificamente ao direcionar contêineres do Windows.


>[!div class="step-by-step"]
[Anterior](what-about-cloud-native-applications.md)
[Próximo](when-not-to-deploy-to-windows-containers.md)
