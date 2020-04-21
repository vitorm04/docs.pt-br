---
title: Implantar aplicativos .NET existentes como contêineres do Windows
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Implantar aplicativos .NET existentes como contêineres do Windows
ms.date: 04/29/2018
ms.openlocfilehash: 15e99e2ec0edd072a3d47d5c212ebbbf6705ecef
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738422"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Implantar aplicativos .NET existentes como contêineres do Windows

As implantações baseadas em contêineres do Windows são aplicáveis a aplicativos otimizados para nuvem e aplicativos nativos da nuvem.

No entanto, neste guia e especialmente nas seções a seguir, ele se concentra principalmente em usar o Windows Containers para aplicativos *otimizados* para nuvem onde você não precisa reprojetar seu aplicativo.

## <a name="what-are-containers-linux-or-windows"></a>O que são contêineres? (Linux ou Windows)

Os contêineres são uma maneira de embrulhar um aplicativo em seu próprio pacote isolado. Em seu contêiner, a aplicação não é afetada por aplicações ou processos que existem fora do contêiner. Tudo o que a aplicação depende para ser executado com sucesso, pois um processo está dentro do contêiner. Onde quer que o contêiner possa se mover, os requisitos do aplicativo serão sempre atendidos, em termos de dependências diretas, pois ele é empacotado com tudo o que precisa para ser executado (dependências de biblioteca, tempos de execução, e assim por diante).

A principal característica de um contêiner é que ele faz com que o ambiente seja o mesmo em diferentes implantações, pois o recipiente em si vem com todas as dependências que precisa. Você pode depurar o aplicativo em sua máquina e, em seguida, implantá-lo em outra máquina, com o mesmo ambiente garantido.

Um contêiner é um exemplo de uma imagem de contêiner. Uma imagem de contêiner é uma maneira de empacotar um aplicativo ou serviço (como um snapshot) e, em seguida, implantá-lo de forma confiável e reprodutível. Pode-se dizer que docker não é apenas uma tecnologia- é também uma filosofia e um processo.

À medida que os contêineres se tornam mais comuns, eles estão se tornando uma "unidade de implantação" em todo o setor.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Benefícios dos contêineres (Docker Engine no Linux ou Windows)

A construção de aplicações usando contêineres - que também podem ser definidos como blocos de construção leves - oferece um aumento significativo na agilidade para construir, enviar e executar qualquer aplicação, em qualquer infra-estrutura.

Com contêineres, você pode levar qualquer aplicativo do desenvolvimento à produção com pouca ou nenhuma alteração de código, graças à integração do Docker entre ferramentas de desenvolvedores da Microsoft, sistemas operacionais e nuvem.

Quando você implanta em VMs simples, você provavelmente já tem um método para implantar aplicativos ASP.NET em suas VMs. É provável, porém, que seu método envolva várias etapas manuais ou processos automatizados complexos usando uma ferramenta de implantação como o Puppet, ou uma ferramenta semelhante. Você pode precisar executar tarefas como modificar itens de configuração, copiar conteúdo de aplicativos entre servidores e executar programas de configuração interativos com base em configurações .msi, seguidos de testes. Todas essas etapas da implantação adicionam tempo e risco às implantações. Você terá falhas sempre que uma dependência não estiver presente no ambiente de destino.

Nos Contêineres Windows, o processo de aplicações de embalagem é totalmente automatizado. O Windows Containers é baseado na plataforma Docker, que oferece atualizações automáticas e reversões para implantações de contêineres. A principal melhoria que você recebe usando o motor Docker é que você cria imagens, que são como instantâneos do seu aplicativo, com todas as suas dependências. As imagens são imagens docker (uma imagem de contêiner do Windows, neste caso). As imagens são executadas ASP.NET aplicativos em contêineres, sem voltar ao código fonte. O instantâneo do contêiner torna-se a unidade de implantação.

Muitas organizações estão contêiner aplicações monolíticas existentes pelas seguintes razões:

- **Liberar agilidade através de uma implantação aprimorada**. Os contêineres oferecem um contrato de implantação consistente entre desenvolvimento e operações. Quando você usa contêineres, você não vai ouvir os desenvolvedores dizerem: "Funciona na minha máquina, por que não na produção?" Eles podem dizer: "Funciona como um contêiner, então ele vai funcionar em produção." O aplicativo embalado, com todas as suas dependências, pode ser executado em qualquer ambiente suportado baseado em contêiner. Ele funcionará da maneira que foi destinado a executar em todos os alvos de implantação (dev, QA, staging, production). Os contêineres eliminam a maioria dos atritos quando passam de um estágio para o outro, o que melhora muito a implantação, e você pode enviar mais rápido.

- **Reduções de custos**. Os contêineres levam a custos mais baixos, seja pela consolidação e remoção do hardware existente, ou pela execução de aplicativos a uma densidade maior por unidade de hardware.

- **Portabilidade**. Os contêineres são modulares e portáteis. Os contêineres Docker são suportados em qualquer sistema operacional de servidor (Linux e Windows), em qualquer nuvem pública importante (Microsoft Azure, Amazon AWS, Google, IBM), e em ambientes de nuvem local e privada ou híbrida.

- **Controle**. Os contêineres oferecem um ambiente flexível e seguro que é controlado ao nível do contêiner. Um contêiner pode ser protegido, isolado e até mesmo limitado definindo políticas de restrição de execução no contêiner. Conforme detalhado na seção sobre contêineres windows, os contêineres Windows Server 2016 e Hyper-V oferecem opções adicionais de suporte corporativo.

Melhorias significativas na agilidade, portabilidade e controle acabam levando a reduções significativas de custos quando você usa contêineres para desenvolver e manter aplicações.

## <a name="what-is-docker"></a>O que é o Docker?

[O Docker](https://www.docker.com/) é um [projeto de código aberto](https://github.com/docker/docker) que automatiza a implantação de aplicativos como contêineres portáteis e auto-suficientes que podem ser executados na nuvem ou no local. O Docker é também um [empresa](https://www.docker.com/) que promove e evolui essa tecnologia. A empresa trabalha em colaboração com fornecedores de nuvem, Linux e Windows, incluindo a Microsoft.

![Diagrama mostrando como o Docker implanta contêineres na nuvem híbrida.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Figura 4-6.** O Docker implanta contêineres em todas as camadas da nuvem híbrida

Para alguém familiarizado com máquinas virtuais, os contêineres podem parecer notavelmente semelhantes. Um contêiner executa um sistema operacional, tem um sistema de arquivos e pode ser acessado em uma rede, assim como um sistema de computador físico ou virtual. No entanto, a tecnologia e os conceitos por trás dos contêineres são muito diferentes das máquinas virtuais. Do ponto de vista do desenvolvedor, um recipiente deve ser tratado mais como um único processo. Na verdade, um contêiner tem um único ponto de entrada para um processo.

Os contêineres Docker (para simplicidade, *contêineres)* podem ser executados nativamente no Linux e no Windows. Ao executar contêineres regulares, os contêineres do Windows podem ser executados apenas em hosts do Windows (um servidor host ou uma VM), e os contêineres Linux podem ser executados apenas em hosts Linux. No entanto, em versões recentes de contêineres Windows Server e Hyper-V, um contêiner Linux também pode ser executado nativamente no Windows Server usando a tecnologia de isolamento Hyper-V que atualmente está disponível apenas em Contêineres do Windows Server.

Em um futuro próximo, ambientes mistos que possuem contêineres Linux e Windows serão possíveis e até comuns.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Benefícios dos contêineres do Windows para seus aplicativos .NET existentes

Os benefícios de usar o Windows Containers são fundamentalmente os mesmos benefícios que você recebe dos contêineres em geral. Usar o Windows Containers é melhorar muito a agilidade, a portabilidade e o controle.

Os aplicativos .NET existentes referem-se aos aplicativos criados usando o .NET Framework. Por exemplo, eles podem ser tradicionais ASP.NET aplicativos web - eles não usam o .NET Core, que é mais novo e executa multiplataforma no Linux, Windows e MacOS.

A principal dependência no Quadro .NET é o Windows. Ele também tem dependências secundárias, como iIS, e System.Web em ASP.NET tradicionais.

Um aplicativo .NET Framework deve ser executado no Windows, ponto final. Se você quiser contêiner os aplicativos existentes do .NET Framework e não puder ou não quiser investir em uma migração para o .NET Core ("Se funcionar corretamente, não migre"), a única opção que você tem para contêineres é usar o Windows Containers.

Então, um dos principais benefícios dos Contêineres windows é que eles oferecem uma maneira de modernizar seus aplicativos .NET Framework existentes que estão sendo executados em contêiner sionário do Windows. Em última análise, o Windows Containers obtém os benefícios que você está procurando usando a agilidade dos contêineres, a portabilidade e o melhor controle.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Escolha um sistema operacional para ser alvo com . Contêineres baseados em NET

Dada a diversidade de sistemas operacionais que são suportados pelo Docker, bem como as diferenças entre .NET Framework e .NET Core, você deve direcionar um Sistema Operacional específico e versões específicas com base na estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows fornecem características diferentes (como IIS versus um servidor web auto-hospedado como o Kestrel) que podem ser necessárias por aplicativos .NET Framework ou .NET Core.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

A Figura 4-7 mostra versões do SO que você pode segmentar, dependendo da versão do aplicativo do .NET Framework.

![Diagrama mostrando qual sistema operacional ser alvo com base na versão .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Figura 4-7.** Sistemas operacionais para segmentação com base na versão .NET Framework

Em cenários de migração para aplicativos existentes ou legados que são baseados em aplicativos .NET Framework, as principais dependências estão no Windows e no IIS. Sua única opção é usar imagens Docker baseadas no Windows Server Core e no .NET Framework.

Quando você adiciona o nome da imagem ao arquivo Dockerfile, você pode selecionar o sistema operacional e a versão usando uma tag, como nos exemplos a seguir para imagens de contêiner do Windows baseadas em framework .NET:

> | **Tag** | **Sistema e versão** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET Framework 4.x no Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET Framework 4.x com personalização adicional de ASP.NET, no Windows Server Core |

Para .NET Core (multiplataforma para Linux e Windows), as tags se pareceriam com as seguintes:

> | **Tag** | **Sistema e versão**
> |---|---|
> | **microsoft/dotnet:2.0.0-tempo de execução** | .NET Core 2.0 somente em execução no Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET Core 2.0 somente em execução no Windows Nano Server |

### <a name="multi-arch-images"></a>Imagens multi-arco

A partir de meados de 2017, você também pode usar um novo recurso no Docker chamado [imagens multi-arco.](https://github.com/moby/moby/issues/15866) As imagens do .NET Core Docker podem usar tags multi-arco. Seus arquivos Dockerfile não precisam mais definir o sistema operacional que você está mirando. O recurso multi-arco permite que uma única tag seja usada em várias configurações da máquina. Por exemplo, com o multi-arco, você pode usar uma tag comum: **microsoft/dotnet:2.0.0-runtime**. Se você puxar essa tag de um ambiente de contêiner Linux, você terá a imagem baseada no Debian. Se você puxar essa tag de um ambiente de contêiner do Windows, você terá a imagem baseada no Nano Server.

Para imagens .NET Framework, porque o tradicional .NET Framework suporta apenas o Windows, você não pode usar o recurso multi-arch.

## <a name="windows-container-types"></a>Tipos de contêineres do Windows

Como os contêineres Linux, os contêineres do Windows Server são gerenciados usando o Docker Engine. Ao contrário dos contêineres Linux, os contêineres do Windows incluem dois tipos diferentes de contêineres, ou executar contêineres do Windows Server e isolamento Hyper-V.

**Contêineres do Windows Server**: Fornece isolamento de aplicativos através de tecnologia de isolamento de processo e namespace. Um contêiner do Windows Server compartilha um kernel com o host de contêiner e todos os contêineres que estão sendo executados no host. Esses contêineres não fornecem um limite de segurança hostil e não devem ser usados para isolar código não confiável. Devido ao espaço de kernel compartilhado, esses contêineres exigem a mesma versão e configuração de kernel.

**Isolamento Hiper-V**: Expande-se no isolamento fornecido pelos contêineres do Windows Server, executando cada contêiner em uma VM altamente otimizada. Nessa configuração, o kernel do host do contêiner não é compartilhado com outros contêineres no mesmo host. Estes contêineres são projetados para hospedagem multilocatário hostil, com as mesmas garantias de segurança de uma VM. Como esses contêineres não compartilham o kernel com o host ou outros contêineres no host, eles podem executar kernels com diferentes versões e configurações (com versões suportadas). Por exemplo, todos os contêineres do Windows no Windows 10 usam isolamento Hyper-V para utilizar a versão e configuração do kernel do Windows Server.

Executar um contêiner no Windows com ou sem isolamento Hyper-V é uma decisão em tempo de execução. Você pode optar por criar o contêiner com isolamento Hyper-V inicialmente e, em tempo de execução, optar por executá-lo como um contêiner do Windows Server.

### <a name="additional-resources"></a>Recursos adicionais

- **Documentação do Windows Containers**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Fundamentos do Windows Containers**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infográfico: Microsoft e contêineres**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>O ecossistema de contêineres no Azure

Em seções anteriores, foi explicado quais são os benefícios dos contêineres Docker, bem como detalhes sobre as imagens específicas de contêiner para aplicações .NET. Todas essas informações genéricas são fundamentais para desenvolver ou contêiner uma aplicação.
No entanto, ao pensar no ambiente de implantação de produção ou mesmo nos ambientes qa e dev/test, o Microsoft Azure fornece uma variedade aberta e ampla de opções, um ecossistema completo de contêineres na nuvem (mostrado no diagrama abaixo). Dependendo das necessidades de sua aplicação específica, você deve escolher um ou outro produto Azure.

![Diagrama do ecossistema de contêineres no Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Figura 4-7.5.** O ecossistema de contêineres no Azure

Do ecossistema de contêineres no Azure, os seguintes produtos que suportam contêineres considerados infra-estrutura:

- **Aci (ACI)**
- **Máquinas virtuais do Azure** (com suporte a contêineres)
- **Conjuntos de escala de máquinavirtual do Azure** (com suporte ao contêiner)

Desses três, a ACI proporciona um grande benefício, que é o fato de que você não precisa manter o sistema operacional subjacente, não há necessidade de você atualizar/patch, etc. mas a ACI ainda está posicionada no nível de infra-estrutura, como melhor explicado nas próximas seções deste livro.

Os produtos em contêineres de suporte a Azure que estão ao mesmo tempo posicionados mais no nível PaaS (Platform as a Service) são:

- **Serviço de Aplicativo do Azure**
- **Serviço Azure Kubernetes (AKS e ACS)**
- **Lote do Azure**

Em seguida, o Registro de Contêineres do Azure é um registro de contêiner escalável de alto nível hospedado no Azure que você pode usar de todos os produtos anteriores ao registrar e implantar suas imagens personalizadas de contêiner.

Além disso, a partir de seus contêineres, você pode consumir outros serviços gerenciados no Azure como O Banco de Dados SQL Do Azure, cache Azure Redis, Azure Cosmos DB, etc. além disso, existem soluções/plataformas de terceiros disponíveis no Azure Marketplace, como Cloud Foundry e OpenShift, onde você também pode usar contêineres dentro do Azure.

Nas próximas seções, você pode explorar as recomendações da Microsoft sobre quando usar cada um desses produtos e soluções do Azure especificamente ao direcionar os contêineres do Windows.

>[!div class="step-by-step"]
>[Próximo](what-about-cloud-native-applications.md)
>[anterior](when-not-to-deploy-to-windows-containers.md)
