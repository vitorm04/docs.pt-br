---
title: Implantar aplicativos .NET existentes como contêineres do Windows
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Implantar aplicativos .NET existentes como contêineres do Windows
ms.date: 04/29/2018
ms.openlocfilehash: ba9af3fc3a5bf285830bb873fa6a5da8390dc6b4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758838"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Implantar aplicativos .NET existentes como contêineres do Windows

Implantações baseadas em contêineres do Windows são aplicáveis aos aplicativos otimizados para a nuvem e aplicativos nativos de nuvem.

No entanto, neste guia e especialmente nas seções a seguir, ele principalmente se concentra no uso dos contêineres do Windows para *otimizada para a nuvem* aplicativos em que você não precisará refazer a arquitetura de seu aplicativo.

## <a name="what-are-containers-linux-or-windows"></a>O que são contêineres? (Linux ou Windows)

Contêineres são uma maneira para empacotar um aplicativo em seu próprio pacote isolado. Em seu contêiner, o aplicativo não é afetado por aplicativos ou processos que existem fora do contêiner. Tudo o que o aplicativo depende a execução com êxito como um processo é dentro do contêiner. Onde quer que o contêiner pode mover, os requisitos do aplicativo sempre serão atendidos, em termos de dependências diretas, pois ele é fornecido com tudo o que ele precisa ser executado (dependências de biblioteca, tempos de execução e assim por diante).

A principal característica de um contêiner é que ele faz o ambiente o mesmo entre diferentes implantações como o contêiner em si é fornecido com todas as dependências necessárias. Você pode depurar o aplicativo em seu computador e, em seguida, implantá-lo em outro computador, com o mesmo ambiente garantido.

Um contêiner é uma instância de uma imagem de contêiner. Uma imagem de contêiner é uma maneira de empacotar um aplicativo ou serviço (como um instantâneo) e, em seguida, implantá-lo de forma confiável e reproduzível. Você poderia dizer que o Docker não é que apenas uma tecnologia-it da também uma filosofia e um processo.

Como contêineres diariamente se tornado mais comuns, eles estão se tornando todo o setor um "unidade de implantação".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Benefícios de contêineres (mecanismo do Docker no Linux ou Windows)

Também criando aplicativos usando contêineres, o que pode ser definido como ofertas de blocos de construção leves um aumento significativo na agilidade para compilar, enviar e executar qualquer aplicativo, em qualquer infraestrutura.

Com os contêineres, você pode aproveitar qualquer aplicativo do desenvolvimento à produção com pouca ou nenhuma alteração de código, graças à integração de Docker em ferramentas de desenvolvedor da Microsoft, de sistemas operacionais e de nuvem.

Quando você implanta em VMs sem formatação, você provavelmente já tem um método em vigor para a implantação de aplicativos do ASP.NET para suas VMs. No entanto, é provável, que o seu método envolve várias etapas manuais ou automatizados de processos complexos usando uma ferramenta de implantação como o Puppet, ou uma ferramenta semelhante. Você talvez precise executar tarefas como modificar itens de configuração, copiar o conteúdo do aplicativo entre os servidores e execução de programas de instalação interativa, com base em configurações. msi, seguidas pelo teste. Todas essas etapas na implantação adicionam tempo e o risco em implantações. Você receberá falhas sempre que uma dependência não está presente no ambiente de destino.

Em contêineres do Windows, o processo de empacotamento de aplicativos é totalmente automatizado. Contêineres do Windows se baseia na plataforma do Docker, que oferece as atualizações automáticas e reversões para implantações de contêiner. O principal aprimoramento obtidos ao usar o mecanismo do Docker é que você crie imagens, que são como os instantâneos do seu aplicativo, com todas as suas dependências. As imagens são imagens do Docker (uma Windows imagem de contêiner, neste caso). As imagens de executar aplicativos ASP.NET em contêineres, sem precisar voltar ao código-fonte. O instantâneo do contêiner torna-se a unidade de implantação.

Muitas organizações estão colocar em contêineres aplicativos monolíticos existentes pelos seguintes motivos:

- **Versão maior agilidade por meio de implantação aprimoradas**. Os contêineres oferecem um contrato de implantação consistente entre o desenvolvimento e operações. Quando você usa contêineres, você não ouvirá os desenvolvedores dizem, "Funciona no meu computador, por que não em produção?" Pode dizer: "Ele é executado como um contêiner, ele será executado na produção." O aplicativo empacotado, com todas as suas dependências, pode ser executado em qualquer ambiente compatível com base em contêiner. Ela será executada da maneira que ele deve ser executado em todos os destinos de implantação (desenvolvimento, QA, preparo e produção). Contêineres eliminam a maioria dos fricções quando eles se movem de um estágio para o próximo, o que melhora significativamente a implantação, e você pode enviar mais rápido.

- **Reduções de custos**. Contêineres de levam a reduzir os custos, pela consolidação e a remoção de hardware existente ou de aplicativos em execução em uma densidade mais alta por unidade de hardware.

- **Portabilidade**. Contêineres são modulares e portátil. Contêineres do docker têm suporte em qualquer sistema operacional (Linux e Windows), em qualquer nuvem pública principais (Microsoft Azure, Amazon AWS, Google e IBM) e no local e privado ou ambientes de nuvem híbrida.

- **Controle**. Os contêineres oferecem um ambiente flexível e seguro que é controlado no nível do contêiner. Um contêiner pode ser protegido, isolado e limitado até mesmo, definindo políticas de restrição de execução no contêiner. Conforme detalhado na seção sobre contêineres do Windows, contêineres do Hyper-V e do Windows Server 2016 oferecem opções de suporte da empresa adicionais.

Aprimoramentos significativos na agilidade, portabilidade e controle acabar levam para reduções significativas nos custos ao usar contêineres para desenvolver e manter aplicativos.

## <a name="what-is-docker"></a>O que é o Docker?

[Docker](https://www.docker.com/) é um [projeto de código-fonte aberto](https://github.com/docker/docker) que automatiza a implantação de aplicativos como contêineres autossuficientes portáteis que podem ser executados na nuvem ou local. O Docker é também um [empresa](https://www.docker.com/) que promove e evolui essa tecnologia. A empresa funciona em colaboração com fornecedores do Windows, incluindo a Microsoft e de nuvem, o Linux.

![](./media/image6.png)

> **Figura 4 a 6.** O Docker implanta contêineres em todas as camadas da nuvem híbrida

Para alguém familiarizado com as máquinas virtuais, contêineres podem parecer muito semelhante. Um contêiner executa um sistema operacional, tem um sistema de arquivos e pode ser acessado em uma rede, assim como um sistema de computador físico ou virtual. No entanto, a tecnologia e os conceitos por trás de contêineres são muito diferentes das máquinas virtuais. Do ponto de vista do desenvolvedor, um contêiner deve ser tratado mais como um único processo. Na verdade, um contêiner tem um único ponto de entrada para um processo.

Contêineres do docker (para manter a simplicidade, *contêineres*) podem ser executados nativamente no Linux e Windows. Ao executar contêineres regulares, os contêineres do Windows podem executar somente em hosts do Windows (um servidor de host ou uma máquina virtual) e contêineres do Linux podem ser executado somente em hosts Linux. No entanto, em versões recentes do Windows Server e Hyper-V contêineres, um contêiner do Linux também pode executar nativamente no Windows Server usando a tecnologia de isolamento do Hyper-V que está atualmente disponível apenas em contêineres do Windows Server.

Em um futuro próximo, ambientes mistos que tenham contêineres do Linux e Windows será possível e até mesmo comum.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Benefícios dos contêineres do Windows para seus aplicativos .NET existentes

Os benefícios do uso de contêineres do Windows são basicamente os mesmos benefícios que você obtém de contêineres em geral. Usando contêineres do Windows é sobre como melhorar bastante a agilidade, portabilidade e controle.

Aplicativos .NET existentes se referem a esses aplicativos que foram criados usando o .NET Framework. Por exemplo, eles podem ser tradicionais aplicativos de web do ASP.NET-eles não usam o .NET Core, que é mais recente e é executado entre plataformas no Linux, Windows e MacOS.

A principal dependência no .NET Framework é Windows. Ele também tem dependências secundárias, como IIS e System. Web no ASP.NET tradicional.

Um aplicativo do .NET Framework deve ser executado no Windows, período. Se você deseja colocar em contêineres de aplicativos .NET Framework existentes e você não pode ou não quiser investir em uma migração para o .NET Core ("se ele está funcionando corretamente, não migrá-la"), a única opção que você tem para contêineres é usar contêineres do Windows.

Portanto, um dos principais benefícios dos contêineres do Windows é que eles oferecem uma maneira para modernizar seus aplicativos existentes do .NET Framework que são executados em contêineres por meio do Windows. Por fim, contêineres do Windows obtém os benefícios que você está procurando usando contêineres de agilidade, portabilidade e um melhor controle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Escolha um sistema operacional direcionar com. Contêineres baseados em NET

Dada a diversidade de sistemas operacionais que são compatíveis com o Docker, bem como as diferenças entre o .NET Framework e .NET Core, você deve ter como destino um sistema operacional específico e em versões específicas com base na estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows oferecem características diferentes (como o IIS em vez de um servidor web auto-hospedado como Kestrel) que podem ser necessários para aplicativos do .NET Framework ou .NET Core.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Figura 4 a 7 mostra as versões do sistema operacional que você pode direcionar, dependendo da versão do aplicativo do .NET Framework.

![](./media/image7.png)

> **Figura 4 a 7.** Sistemas operacionais de destino com base na versão do .NET Framework

Em cenários de migração para aplicativos existentes ou herdados que se baseiam em aplicativos do .NET Framework, as dependências principais são no Windows e no IIS. Sua única opção é usar imagens do Docker com base no Windows Server Core e o .NET Framework.

Quando você adiciona o nome da imagem ao seu arquivo Dockerfile, você pode selecionar o sistema operacional e a versão por meio de uma marca, como nos exemplos a seguir para imagens de contêiner do Windows com base no .NET Framework:

> | **Tag** | **Versão e sistema** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x no Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x com personalização adicional do ASP.NET, no Windows Server Core |

Para o .NET Core (plataforma cruzada para Linux e Windows), as marcas teriam a seguinte aparência:

> | **Tag** | **Versão e sistema**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 em tempo de execução somente no Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Tempo de execução somente no Windows Nano Server do .NET core 2.0 |

### <a name="multi-arch-images"></a>Imagens de várias arquiteturas

A partir de meados de 2017, você também pode usar um novo recurso no Docker chamado [várias arquiteturas](https://github.com/moby/moby/issues/15866) imagens. Imagens do Docker no .NET core podem usar marcas para várias arquiteturas. Arquivos de seu Dockerfile não há mais necessidade de definir o sistema operacional de destino. O recurso para várias arquiteturas permite uma única marca a ser usado em várias configurações de máquina. Por exemplo, com várias arquiteturas, você pode usar uma marca comuns: **microsoft/dotnet:2.0.0-runtime**. Se você puxar a marca de um ambiente de contêiner do Linux, você obtém a imagem com base em Debian. Se você puxar a marca de um ambiente de contêiner do Windows, você obtém a imagem baseada em Nano Server.

Para imagens do .NET Framework, como o .NET Framework tradicional oferece suporte somente a Windows, é possível usar o recurso para várias arquiteturas.

## <a name="windows-container-types"></a>Tipos de contêineres do Windows

Como contêineres do Linux, contêineres do Windows Server são gerenciados usando o mecanismo do Docker. Ao contrário de contêineres do Linux, contêineres do Windows incluem dois tipos de contêiner diferente, ou executam contêineres do Windows vezes Server e o isolamento do Hyper-V.

**Contêineres do Windows Server**: Fornece isolamento de aplicativo por meio da tecnologia de isolamento de processo e de namespace. Um contêiner do Windows Server compartilha um kernel com o host do contêiner e todos os contêineres que estão em execução no host. Esses contêineres não fornecem um limite de segurança hostil e não devem ser usados para isolar o código não confiável. Por causa do espaço de kernel compartilhado, esses contêineres exigem a mesma versão do kernel e a configuração.

**Isolamento do Hyper-V**: Expande o isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma máquina virtual altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com outros contêineres no mesmo host. Esses contêineres são projetados para hospedar vários locatários hostis, a com as mesmas garantias de segurança de uma VM. Como esses contêineres não compartilham o kernel com o host ou outros contêineres no host, eles podem executar kernels com diferentes versões e configurações (com as versões com suporte). Por exemplo, todos os contêineres do Windows no Windows 10 usam isolamento do Hyper-V para utilizar a versão do kernel do Windows Server e a configuração.

Executar um contêiner no Windows, com ou sem o isolamento do Hyper-V é uma decisão de tempo de execução. Você pode optar por criar o contêiner com o isolamento do Hyper-V inicialmente e, em tempo de execução, optar por executá-lo como um contêiner do Windows Server.

### <a name="additional-resources"></a>Recursos adicionais

- **Documentação de contêineres do Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Conceitos básicos de contêineres do Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infográfico: A Microsoft e contêineres**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>O ecossistema de contêiner no Azure

Nas seções anteriores, ele tem sido explicado quais são os benefícios de contêineres do Docker, bem como detalhes sobre as imagens de contêiner específico para aplicativos .NET. Obter informações genéricas tudo o que são fundamentais para desenvolver ou colocar em contêiner um aplicativo.
No entanto, ao pensar sobre o ambiente de implantação de produção ou até mesmo os ambientes de desenvolvimento/teste e controle de qualidade, o Microsoft Azure fornece uma aberta e ampla variedade de opções, um ecossistema de contêiner completa na nuvem (mostrado no diagrama abaixo). Dependendo das necessidades do seu aplicativo específico, você deve escolher um ou outro produto do Azure.

![](./media/image7.5.png)

> **Figura 4-7.5.** O ecossistema de contêiner no Azure

No ecossistema do contêiner no Azure, os seguintes produtos que dão suporte a contêineres que são considerados infraestrutura:
- **Instâncias de contêiner do Azure (ACI)**
- **Máquinas virtuais do Azure** (com suporte do contêiner)
- **Conjuntos de dimensionamento de máquina Virtual do Azure** (com suporte do contêiner)

De um desses três, a ACI oferece um grande benefício é o fato de que você não precisa manter o sistema operacional subjacente, você não precisa atualizar/aplicar patch, etc., mas ainda ACI é posicionado no nível de infraestrutura, como melhor explicado nas próximas seções deste livro.

Os produtos em contêineres de suporte do Azure que estão ao mesmo tempo mais posicionado na PaaS (plataforma como serviço) níveis são:

- **Serviço de Aplicativo do Azure**
- **Serviço Kubernetes do Azure (AKS e ACS)**
- **Azure Batch** 

Em seguida, o registro de contêiner do Azure é um registro de contêiner escalonável alta hospedado no Azure que você pode usar de todos os produtos anteriores durante o registro e implantar suas imagens de contêiner personalizado.

Além disso, de seus contêineres, você pode consumir outros serviços gerenciados no Azure como o banco de dados SQL, cache Redis do Azure, Azure Cosmos DB, etc. Além disso, há plataformas/soluções de terceiros disponíveis no Azure Marketplace, como o Cloud Foundry e OpenShift em que você também pode usar contêineres dentro do Azure. 

Nas próximas seções, você pode explorar as recomendações da Microsoft sobre quando usar cada um desses produtos do Azure e soluções especificamente ao direcionar a contêineres do Windows.

>[!div class="step-by-step"]
>[Anterior](what-about-cloud-native-applications.md)
>[Próximo](when-not-to-deploy-to-windows-containers.md)
