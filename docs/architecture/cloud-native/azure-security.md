---
title: Segurança do Azure para aplicativos nativos da nuvem
description: Arquitetando aplicativos nativos da nuvem .NET para Azure | Segurança do Azure para aplicativos nativos da nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 13b5ad7a883a83014913fa0a6a020610c28c524f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989136"
---
# <a name="azure-security-for-cloud-native-apps"></a>Segurança do Azure para aplicativos nativos da nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplicativos nativos da nuvem podem ser mais fáceis e difíceis de proteger do que os aplicativos tradicionais. No lado negativo, você precisa proteger aplicativos mais menores e dedicar mais energia para construir a infra-estrutura de segurança. A natureza heterogênea das linguagens e estilos de programação na maioria das implantações de serviços também significa que você precisa prestar mais atenção aos boletins de segurança de muitos provedores diferentes.

Por outro lado, serviços menores, cada um com seu próprio armazenamento de dados, limitam o escopo de um ataque. Se um atacante compromete um sistema, provavelmente é mais difícil para o atacante fazer o salto para outro sistema do que em uma aplicação monolítica. Os limites do processo são limites fortes. Além disso, se um backup de banco de dados vazar, então o dano é mais limitado, pois esse banco de dados contém apenas um subconjunto de dados e é improvável que contenha dados pessoais.

## <a name="threat-modeling"></a>Modelagem de ameaças

Não importa se as vantagens superam as desvantagens dos aplicativos nativos da nuvem, a mesma mentalidade de segurança holística deve ser seguida. Segurança e pensamento seguro devem fazer parte de cada etapa da história de desenvolvimento e operações. Ao planejar um aplicativo, faça perguntas como:

- Qual seria o impacto dessa perda de dados?
- Como podemos limitar os danos causados pela injeção de dados ruins neste serviço?
- Quem deve ter acesso a esses dados?
- Existem políticas de auditoria em torno do processo de desenvolvimento e liberação?

Todas essas perguntas fazem parte de um processo chamado [modelagem de ameaças.](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool) Este processo tenta responder à questão de quais ameaças existem ao sistema, quão prováveis são as ameaças e os danos potenciais delas.

Uma vez estabelecida a lista de ameaças, você precisa decidir se elas valem a pena mitigar. Às vezes, uma ameaça é tão improvável e cara de planejar que não vale a pena gastar energia com ela. Por exemplo, algum ator de nível estadual poderia injetar mudanças no design de um processo que é usado por milhões de dispositivos. Agora, em vez de executar um certo pedaço de código no [Anel 3,](https://en.wikipedia.org/wiki/Protection_ring)esse código é executado no Anel 0. Isso permite uma exploração que pode contornar o hipervisor e executar o código de ataque nas máquinas de metal nuas, permitindo ataques em todas as máquinas virtuais que estão sendo executadas nesse hardware.

Os processadores alterados são difíceis de detectar sem um microscópio e conhecimento avançado do design em silício desse processador. Esse cenário é improvável de acontecer e caro para mitigar, então provavelmente nenhum modelo de ameaça recomendaria construir proteção de exploração para ele.

Ameaças mais prováveis, como controles de `Id` acesso quebrados `Id=2` que `Id=3` permitem ataques incrementais (substituindo na URL) ou injeção SQL, são mais atraentes para construir proteções contra. As atenuações para essas ameaças são bastante razoáveis para construir e evitar falhas de segurança embaraçosas que mancham a reputação da empresa.

## <a name="principle-of-least-privilege"></a>Princípio de privilégios mínimos

Uma das ideias fundadoras em segurança de computadores é o Princípio do Menor Privilégio (POLP). Na verdade, é uma ideia fundamental na maioria das formas de segurança, seja digital ou física. Em suma, o princípio é que qualquer usuário ou processo deve ter o menor número de direitos possíveis para executar sua tarefa.

Como exemplo, pense nos caixas de um banco: acessar o cofre é uma atividade incomum. Então, o caixa médio não pode abrir o cofre sozinho. Para ter acesso, eles precisam intensificar sua solicitação através de um gerente de banco, que realiza verificações adicionais de segurança.

Em um sistema de computador, um exemplo fantástico são os direitos de um usuário se conectar a um banco de dados. Em muitos casos, há uma única conta de usuário usada para construir a estrutura do banco de dados e executar o aplicativo. Exceto em casos extremos, a conta que executa o aplicativo não precisa da capacidade de atualizar informações de esquema. Deve haver várias contas que fornecem diferentes níveis de privilégio. O aplicativo só deve usar o nível de permissão que concede acesso à leitura e gravação aos dados nas tabelas. Esse tipo de proteção eliminaria ataques que visavam derrubar tabelas de banco de dados ou introduzir gatilhos maliciosos.

Quase todas as partes da construção de um aplicativo nativo em nuvem podem se beneficiar de lembrar o princípio do menor privilégio. Você pode encontrá-lo em jogo ao configurar firewalls, grupos de segurança de rede, funções e escopos no RBAC (Role-based Access Control, controle de acesso baseado em funções).

## <a name="penetration-testing"></a>Testes de penetração

À medida que as aplicações se tornam mais complicadas, o número de vetores de ataque aumenta a uma taxa alarmante. A modelagem de ameaças é falha na pois tende a ser executada pelas mesmas pessoas que constroem o sistema. Da mesma forma que muitos desenvolvedores têm dificuldade em imaginar interações do usuário e, em seguida, construir interfaces de usuário inutilizáveis, a maioria dos desenvolvedores tem dificuldade em ver cada vetor de ataque. Também é possível que os desenvolvedores que constroem o sistema não sejam bem versados em metodologias de ataque e percam algo crucial.

Testes de penetração ou "teste de caneta" envolvem trazer atores externos para tentar atacar o sistema. Esses invasores podem ser uma empresa de consultoria externa ou outros desenvolvedores com bom conhecimento de segurança de outra parte do negócio. Eles têm carta branca para tentar subverter o sistema. Freqüentemente, eles encontrarão extensas falhas de segurança que precisam ser corrigidas. Às vezes, o vetor de ataque será algo totalmente inesperado como explorar um ataque de phishing contra o CEO.

O próprio Azure está constantemente sofrendo ataques de uma [equipe de hackers dentro da Microsoft](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/). Ao longo dos anos, eles foram os primeiros a encontrar dezenas de vetores de ataque potencialmente catastróficos, fechando-os antes que possam ser explorados externamente. Quanto mais tentador um alvo, mais provável é que atores eternos tentem explorá-lo e há alguns alvos no mundo mais tentadores do que o Azure.

## <a name="monitoring"></a>Monitoramento

Se um invasor tentar penetrar uma aplicação, deve haver algum aviso sobre isso. Frequentemente, os ataques podem ser detectados examinando os registros dos serviços. Ataques deixam sinais que podem ser vistos antes de terem sucesso. Por exemplo, um invasor que tentar adivinhar uma senha fará muitas solicitações para um sistema de login. O monitoramento ao redor do sistema de login pode detectar padrões estranhos que estão fora de linha com o padrão de acesso típico. Esse monitoramento pode ser transformado em um alerta que pode, por sua vez, alertar uma pessoa de operações para ativar algum tipo de contramedida. Um sistema de monitoramento altamente maduro pode até mesmo agir com base nesses desvios adicionando regras proativamente para bloquear solicitações ou respostas do acelerador.

## <a name="securing-the-build"></a>Protegendo a construção

Um lugar onde a segurança é muitas vezes negligenciada é em torno do processo de compilação. Não só as verificações de segurança de execução de compilação, como a varredura de código inseguro ou credenciais de check-in, mas a compilação em si deve ser segura. Se o servidor de compilação estiver comprometido, ele fornecerá um vetor fantástico para introduzir código arbitrário no produto.

Imagine que um invasor está procurando roubar as senhas de pessoas que entram em um aplicativo web. Eles poderiam introduzir uma etapa de compilação que modifica o código de check-out para espelhar qualquer solicitação de login para outro servidor. Da próxima vez que o código passar pela compilação, é silenciosamente atualizado. A varredura de vulnerabilidade do código fonte não vai pegar isso enquanto é executado antes da compilação. Da mesma forma, ninguém vai pegá-lo em uma revisão de código porque as etapas de compilação vivem no servidor de compilação. O código explorado irá para a produção onde pode coletar senhas. Provavelmente não há registro de auditoria das mudanças no processo de construção, ou pelo menos ninguém monitorando a auditoria.

Este é um exemplo perfeito de um alvo de valor aparentemente baixo que pode ser usado para invadir o sistema. Uma vez que um invasor viola o perímetro do sistema, eles podem começar a trabalhar em encontrar maneiras de elevar suas permissões ao ponto de que eles podem causar danos reais em qualquer lugar que eles quiserem.

## <a name="building-secure-code"></a>Construindo código seguro

.NET Framework já é uma estrutura bastante segura. Evita algumas das armadilhas de códigos não gerenciados, como sair das extremidades das matrizes. O trabalho é feito ativamente para corrigir falhas de segurança à medida que são descobertas. Há até um [programa de recompensa de bugs](https://www.microsoft.com/msrc/bounty) que paga aos pesquisadores para encontrar problemas na estrutura e denunciá-los em vez de explorá-los.

Existem muitas maneiras de tornar o código .NET mais seguro. Seguir diretrizes como as [diretrizes de codificação Secure para o](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) artigo .NET é um passo razoável a ser dado para garantir que o código esteja seguro do zero. O [Top 10 do OWASP](https://owasp.org/www-project-top-ten/) é outro guia inestimável para construir código seguro.

O processo de compilação é um bom lugar para colocar ferramentas de digitalização para detectar problemas no código fonte antes de entrar em produção. A maioria dos projetos tem dependências de alguns outros pacotes. Uma ferramenta que pode procurar pacotes desatualizados pegará problemas em uma compilação noturna. Mesmo ao construir imagens do Docker, é útil verificar e certificar-se de que a imagem base não tem vulnerabilidades conhecidas. Outra coisa a verificar é que ninguém acidentalmente verificou credenciais.

## <a name="built-in-security"></a>Segurança incorporada

O Azure foi projetado para equilibrar usabilidade e segurança para a maioria dos usuários. Diferentes usuários terão diferentes requisitos de segurança, então eles precisam ajustar sua abordagem à segurança na nuvem. A Microsoft publica uma grande quantidade de informações de segurança no [Trust Center](https://azure.microsoft.com/support/trust-center/). Esse recurso deve ser a primeira parada para os profissionais interessados em entender como funcionam as tecnologias de mitigação de ataques incorporadas.

Dentro do portal Azure, o [Azure Advisor](https://azure.microsoft.com/services/advisor/) é um sistema que está constantemente digitalizando um ambiente e fazendo recomendações. Algumas dessas recomendações são projetadas para economizar dinheiro dos usuários, mas outras são projetadas para identificar configurações potencialmente inseguras, como ter um contêiner de armazenamento aberto ao mundo e não protegido por uma Rede Virtual.

## <a name="azure-network-infrastructure"></a>Infraestrutura de rede do Azure

Em um ambiente de implantação local, uma grande quantidade de energia é dedicada à configuração de redes. Configurar roteadores, interruptores e isso é um trabalho complicado. As redes permitem que certos recursos conversem com outros recursos e impeçam o acesso em alguns casos. Uma regra de rede freqüente é restringir o acesso ao ambiente de produção do ambiente de desenvolvimento na chance de que um pedaço de código meio desenvolvido seja executado errado e exclua uma faixa de dados.

Fora da caixa, a maioria dos recursos do PaaS Azure tem apenas a configuração de rede mais básica e permissiva. Por exemplo, qualquer pessoa na Internet pode acessar um serviço de aplicativo. Novas instâncias do SQL Server normalmente são restritas, de modo que as partes externas não podem acessá-las, mas as faixas de endereçoIP usadas pelo próprio Azure são permitidas. Assim, enquanto o servidor SQL está protegido contra ameaças externas, um invasor só precisa configurar uma ponte Azure de onde eles podem lançar ataques contra todas as instâncias SQL no Azure.

Felizmente, a maioria dos recursos do Azure pode ser colocada em uma Rede Virtual Azure que permite um controle de acesso mais fino. Semelhante à maneira como as redes locais estabelecem redes privadas protegidas do mundo inteiro, as redes virtuais são ilhas de endereços IP privados que estão localizados dentro da rede Azure.

![Figura 10-1 Uma rede virtual](./media/virtual-network.png)
na Figura Azure**10-1**. Uma rede virtual no Azure.

Da mesma forma que as redes locais têm um firewall que rege o acesso à rede, você pode estabelecer um firewall semelhante no limite da rede virtual. Por padrão, todos os recursos em uma rede virtual ainda podem falar com a Internet. São apenas conexões recebidas que requerem alguma forma de exceção explícita de firewall.

Com a rede estabelecida, recursos internos como contas de armazenamento podem ser configurados para permitir apenas o acesso por recursos que também estão na Rede Virtual. Este firewall fornece um nível extra de segurança, caso as chaves dessa conta de armazenamento sejam vazadas, os atacantes não seriam capazes de se conectar a ela para explorar as chaves vazadas. Este é outro exemplo do princípio do menor privilégio.

Os nós em um cluster Azure Kubernetes podem participar de uma rede virtual, assim como outros recursos mais nativos do Azure. Essa funcionalidade é chamada [de Interface de Rede de Contêineres Do Azure](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md). Na verdade, ele aloca uma sub-rede dentro da rede virtual na qual máquinas virtuais e imagens de contêineres são alocadas.

Continuando o caminho de ilustrar o princípio do menor privilégio, nem todos os recursos dentro de uma Rede Virtual precisam conversar com todos os outros recursos. Por exemplo, em um aplicativo que fornece uma API web sobre uma conta de armazenamento e um banco de dados SQL, é improvável que o banco de dados e a conta de armazenamento precisem conversar entre si. Qualquer compartilhamento de dados entre eles passaria pelo aplicativo web. Assim, um [grupo de segurança de rede (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) poderia ser usado para negar tráfego entre os dois serviços.

Uma política de negar comunicação entre recursos pode ser irritante de implementar, especialmente vindo de um contexto de uso do Azure sem restrições de tráfego. Em algumas outras nuvens, o conceito de grupos de segurança de rede é muito mais prevalente. Por exemplo, a política padrão no AWS é que os recursos não podem se comunicar entre si até ser habilitado por regras em um NSG. Embora mais lento para desenvolver isso, um ambiente mais restritivo fornece um padrão mais seguro. Fazer uso de práticas de DevOps adequadas, especialmente usando [o Azure Resource Manager ou terraform](infrastructure-as-code.md) para gerenciar permissões pode facilitar o controle das regras.

Redes Virtuais também podem ser úteis ao configurar a comunicação entre o local e os recursos em nuvem. Uma rede privada virtual pode ser usada para conectar perfeitamente as duas redes. Isso permite executar uma rede virtual sem qualquer tipo de gateway para cenários onde todos os usuários estão no local. Há uma série de tecnologias que podem ser usadas para estabelecer essa rede. O mais simples é usar uma [VPN site-to-site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) que pode ser estabelecida entre muitos roteadores e o Azure. O tráfego é criptografado e encapsulado pela Internet ao mesmo custo por byte que qualquer outro tráfego. Para cenários onde mais largura de banda ou mais segurança é desejável, o Azure oferece um serviço chamado [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) que usa um circuito privado entre uma rede local e o Azure. É mais caro e difícil de estabelecer, mas também mais seguro.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Controle de acesso baseado em função para restringir o acesso aos recursos do Azure

RBAC é um sistema que fornece uma identidade para aplicativos em execução no Azure. Os aplicativos podem acessar recursos usando essa identidade em vez de ou além de usar chaves ou senhas.

## <a name="security-principals"></a>Entidades de segurança

O primeiro componente no RBAC é um diretor de segurança. Um diretor de segurança pode ser um usuário, grupo, diretor de serviço ou identidade gerenciada.

![Figura 10-2 Diferentes](./media/rbac-security-principal.png)
tipos de princípios de segurança Figura**10-2**. Diferentes tipos de diretores de segurança.

- Usuário - Qualquer usuário que tenha uma conta no Azure Active Directory é um usuário.
- Grupo - Uma coleção de usuários do Azure Active Directory. Como membro de um grupo, um usuário assume as funções desse grupo, além das suas.
- Diretor de serviço - Uma identidade de segurança sob a qual os serviços ou aplicativos são executados.
- Identidade gerenciada - Uma identidade do Diretório Ativo do Azure gerenciada pelo Azure. As identidades gerenciadas são normalmente usadas ao desenvolver aplicativos em nuvem que gerenciam as credenciais para autenticação aos serviços do Azure.

O principal de segurança pode ser aplicado à maioria dos recursos. Isso significa que é possível atribuir um princípio de segurança a um contêiner que está sendo executado dentro do Azure Kubernetes, permitindo que ele acesse segredos armazenados no Key Vault. Uma função Azure pode ter uma permissão que permite que ele converse com uma instância do Active Directory para validar um JWT para um usuário de chamada. Uma vez que os serviços são habilitados com um diretor de serviço, suas permissões podem ser gerenciadas granularmente usando funções e escopos.

## <a name="roles"></a>Funções

Um diretor de segurança pode assumir muitos papéis ou, usando uma analogia mais sartorial, usar muitos chapéus. Cada função define uma série de permissões, como "Ler mensagens do ponto final do Ônibus de Serviço do Azure". O conjunto de permissões eficazes de um diretor de segurança é a combinação de todas as permissões atribuídas a todas as funções que o diretor de segurança tem. O Azure tem um grande número de funções incorporadas e os usuários podem definir suas próprias funções.

![Figura 10-3 Definições](./media/rbac-role-definition.png)
de função RBAC Figura**10-3**. Definições de função RBAC.

Embutido no Azure também há uma série de funções de alto nível, como Proprietário, Contribuinte, Leitor e Administrador de Conta de Usuário. Com a função Proprietário, um diretor de segurança pode acessar todos os recursos e atribuir permissões a outros. Um contribuinte tem o mesmo nível de acesso a todos os recursos, mas não pode atribuir permissões. Um Leitor só pode visualizar os recursos existentes do Azure e um administrador de conta de usuário pode gerenciar o acesso aos recursos do Azure.

Funções incorporadas mais granulares, como [o DNS Zone Contributor,](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) têm direitos limitados a um único serviço. Os diretores de segurança podem assumir qualquer número de funções.

## <a name="scopes"></a>Escopos

As funções podem ser aplicadas a um conjunto restrito de recursos dentro do Azure. Por exemplo, aplicando o escopo ao exemplo anterior de leitura de uma fila de Ônibus de Serviço, você pode reduzir `blah.servicebus.windows.net/queue1`a permissão para uma única fila: "Leia mensagens do ponto final do Ônibus de Serviço do Azure"

O escopo pode ser tão estreito quanto um único recurso ou pode ser aplicado a um grupo inteiro de recursos, assinatura ou até mesmo grupo de gerenciamento.

Ao testar se um diretor de segurança tem uma certa permissão, a combinação de função e escopo são levadas em conta. Esta combinação fornece um poderoso mecanismo de autorização.

## <a name="deny"></a>Negar

Anteriormente, apenas as regras de "permitir" eram permitidas para o RBAC. Esse comportamento tornou alguns escopos complicados de construir. Por exemplo, permitir um acesso principal de segurança a todas as contas de armazenamento, exceto uma necessária concessão de permissão explícita a uma lista potencialmente interminável de contas de armazenamento. Toda vez que uma nova conta de armazenamento fosse criada, ela teria que ser adicionada a essa lista de contas. Isso adicionou sobrecarga de gerenciamento que certamente não era desejável.

As regras de negação têm precedência sobre as regras de permitir. Agora, representando o mesmo escopo "permitir todos, menos um" poderia ser representado como duas regras "permitir todos" e "negar esta específica". Negar regras não só facilita a gestão, mas permite recursos extraseguros, negando acesso a todos.

## <a name="checking-access"></a>Verificando o acesso

Como você pode imaginar, ter um grande número de funções e escopos pode tornar difícil descobrir a permissão efetiva de um diretor de serviço. Empilhar regras de negação em cima disso, só serve para aumentar a complexidade. Felizmente, há uma calculadora de permissões que pode mostrar as permissões eficazes para qualquer diretor de serviço. É normalmente encontrado sob a guia IAM no portal, como mostrado na Figura 10-3.

![Figura 10-4 Calculadora de permissão para um serviço](./media/check-rbac.png)
de aplicativo Figura**10-4**. Calculadora de permissão para um serviço de aplicativo.

## <a name="securing-secrets"></a>Segredo garantindo segredos

Senhas e certificados são um vetor de ataque comum para atacantes. O hardware de quebra de senhas pode fazer um ataque de força bruta e tentar adivinhar bilhões de senhas por segundo. Por isso, é importante que as senhas usadas para acessar recursos sejam fortes, com uma grande variedade de caracteres. Essas senhas são exatamente o tipo de senhas que são quase impossíveis de lembrar. Felizmente, as senhas no Azure não precisam ser conhecidas por nenhum humano.

Muitos [especialistas em](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) segurança sugerem que usar um gerenciador de senhas para manter suas próprias senhas é a melhor abordagem. Embora centralize suas senhas em um local, ele também permite o uso de senhas altamente complexas e a garantia de que elas sejam únicas para cada conta. O mesmo sistema existe dentro do Azure: uma loja central para segredos.

## <a name="azure-key-vault"></a>Cofre de Chave do Azure

O Azure Key Vault fornece um local centralizado para armazenar senhas para coisas como bancos de dados, chaves de API e certificados. Uma vez que um segredo é inserido no Cofre, ele nunca é mostrado novamente e os comandos para extraí-lo e vê-lo são propositalmente complicados. As informações no cofre são protegidas usando criptografia de software ou módulos de segurança de hardware validados pelo FIPS 140-2.

O acesso ao cofre principal é fornecido através de RBACs, o que significa que não apenas qualquer usuário pode acessar as informações no cofre. Digamos que um aplicativo web deseja acessar a seqüência de conexão de banco de dados armazenada no Azure Key Vault. Para ter acesso, os aplicativos precisam ser executados usando um diretor de serviço. Sob este papel assumido, eles podem ler os segredos do cofre. Existem várias configurações de segurança diferentes que podem limitar ainda mais o acesso que um aplicativo tem ao cofre, de modo que ele não pode atualizar segredos, mas apenas lê-los.

O acesso ao cofre principal pode ser monitorado para garantir que apenas os aplicativos esperados estejam acessando o cofre. Os logs podem ser integrados de volta ao Azure Monitor, desbloqueando a capacidade de configurar alertas quando condições inesperadas são encontradas.

## <a name="kubernetes"></a>Kubernetes

Dentro dos Kubernetes, há um serviço semelhante para manter pequenas peças de informação secreta. Kubernetes Secrets pode ser `kubectl` definido através do executável típico.

Criar um segredo é tão simples quanto encontrar a versão base64 dos valores a serem armazenados:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Em seguida, adicioná-lo a um arquivo de segredos nomeado, `secret.yml` por exemplo, que se parece com o seguinte exemplo:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

Finalmente, este arquivo pode ser carregado no Kubernetes executando o seguinte comando:

```console
kubectl apply -f ./secret.yaml
```

Esses segredos podem então ser montados em volumes ou expostos a processos de contêineres através de variáveis ambientais. A abordagem [do aplicativo de doze fatores](https://12factor.net/) para criar aplicativos sugere usar o menor denominador comum para transmitir configurações a um aplicativo. As variáveis de ambiente são o menor denominador comum, porque são suportadas não importa o sistema operacional ou aplicativo.

Uma alternativa para usar os segredos kubernetes incorporados é acessar os segredos no Azure Key Vault de dentro dos Kubernetes. A maneira mais simples de fazer isso é atribuir uma função RBAC ao contêiner que procura carregar segredos. O aplicativo pode então usar as APIs do Azure Key Vault para acessar os segredos. No entanto, essa abordagem requer modificações no código e não segue o padrão de uso de variáveis de ambiente. Em vez disso, é possível injetar valores em um recipiente através do uso do [Azure Key Vault Injector](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354). Essa abordagem é, na verdade, mais segura do que usar os segredos do Kubernetes diretamente, pois eles podem ser acessados pelos usuários no cluster.

## <a name="encryption-in-transit-and-at-rest"></a>Criptografia em trânsito e em repouso

Manter os dados seguros é importante, seja em disco ou transitando entre vários serviços diferentes. A maneira mais eficaz de evitar que os dados vazem é criptografá-los em um formato que não pode ser facilmente lido por outros. O Azure suporta uma ampla gama de opções de criptografia.

### <a name="in-transit"></a>Em trânsito

Existem várias maneiras de criptografar o tráfego na rede no Azure. O acesso aos serviços do Azure é normalmente feito sobre conexões que usam TLS (Transport Layer Security). Por exemplo, todas as conexões com as APIs do Azure requerem conexões TLS. Da mesma forma, as conexões aos pontos finais no armazenamento Azure podem ser restritas apenas para funcionar em conexões criptografadas TLS.

O TLS é um protocolo complicado e simplesmente saber que a conexão está usando TLS não é suficiente para garantir a segurança. Por exemplo, o TLS 1.0 é cronicamente inseguro, e o TLS 1.1 não é muito melhor. Mesmo dentro das versões do TLS, existem várias configurações que podem tornar as conexões mais fáceis de descriptografar. O melhor curso de ação é verificar e ver se a conexão do servidor está usando protocolos atualizados e bem configurados.

Essa verificação pode ser feita por um serviço externo, como o Teste de Servidor SSL dos laboratórios SSL. Um teste executado contra um ponto final típico do Azure, neste caso um ponto final de ônibus de serviço, rende uma pontuação quase perfeita de A.

Mesmo serviços como bancos de dados SQL do Azure usam criptografia TLS para manter os dados escondidos. A parte interessante sobre criptografar os dados em trânsito usando TLS é que não é possível, mesmo para a Microsoft, ouvir a conexão entre computadores que executam O TLS. Isso deve fornecer conforto para as empresas preocupadas que seus dados possam estar em risco da Microsoft própria ou até mesmo de um ator estatal com mais recursos do que o invasor padrão.

![Figura 10-5 relatório ssl labs mostrando uma pontuação de A para um ponto final de ônibus de serviço. ](./media/ssl-report.png)
 **Figura 10-5**. Relatório ssl labs mostrando uma pontuação de A para um ponto final de ônibus de serviço.

Embora esse nível de criptografia não seja suficiente para todos os tempos, deve inspirar confiança de que as conexões Azure TLS são bastante seguras. O Azure continuará a evoluir seus padrões de segurança à medida que a criptografia melhorar. É bom saber que há alguém observando os padrões de segurança e atualizando o Azure à medida que eles melhoram.

### <a name="at-rest"></a>Em repouso

Em qualquer aplicativo, há uma série de lugares onde os dados repousam no disco. O próprio código do aplicativo é carregado a partir de algum mecanismo de armazenamento. A maioria dos aplicativos também usa algum tipo de banco de dados, como SQL Server, Cosmos DB ou mesmo o incrivelmente eficiente armazenamento de mesa. Todos esses bancos de dados usam armazenamento altamente criptografado para garantir que ninguém além dos aplicativos com permissões adequadas possa ler seus dados. Nem mesmo os operadores do sistema podem ler dados criptografados. Assim, os clientes podem permanecer confiantes de que suas informações secretas permanecem em segredo.

### <a name="storage"></a>Armazenamento

A base de grande parte do Azure é o motor Azure Storage. Os discos da máquina virtual são montados em cima do Armazenamento Azure. O Azure Kubernetes Services é executado em máquinas virtuais que, por si só, estão hospedadas no Azure Storage. Mesmo tecnologias sem servidor, como aplicativos de funções do Azure e instâncias de contêiner do Azure, ficam sem disco que faz parte do Azure Storage.

Se o Azure Storage é bem criptografado, então ele fornece uma base para que a maioria dos outros também seja criptografada. O Azure Storage [é criptografado](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) com [Fips 140-2](https://en.wikipedia.org/wiki/FIPS_140) compatíveis com AES de [256 bits](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard). Esta é uma tecnologia de criptografia bem conceituada tendo sido objeto de extenso escrutínio acadêmico nos últimos 20 anos. No momento, não há nenhum ataque prático conhecido que permita a alguém sem conhecimento da chave ler dados criptografados pela AES.

Por padrão, as chaves usadas para criptografar o Azure Storage são gerenciadas pela Microsoft. Existem extensas proteções para garantir o acesso malicioso a essas chaves. No entanto, usuários com requisitos específicos de criptografia também podem [fornecer suas próprias chaves de armazenamento](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) que são gerenciadas no Azure Key Vault. Essas chaves podem ser revogadas a qualquer momento, o que efetivamente tornaria o conteúdo da conta de armazenamento usando-as inacessíveis.

As máquinas virtuais usam armazenamento criptografado, mas é possível fornecer outra camada de criptografia usando tecnologias como BitLocker no Windows ou DM-Crypt no Linux. Essas tecnologias significam que, mesmo que a imagem do disco tenha vazado do armazenamento, ela permaneceria quase impossível de lê-la.

### <a name="azure-sql"></a>SQL do Azure

Os bancos de dados hospedados no Azure SQL usam uma tecnologia chamada [Transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) para garantir que os dados permaneçam criptografados. Ele é ativado por padrão em todos os bancos de dados SQL recém-criados, mas deve ser habilitado manualmente para bancos de dados legados. O TDE executa criptografia e descriptografia em tempo real não apenas do banco de dados, mas também dos backups e logs de transações.

Os parâmetros de `master` criptografia são armazenados no banco de dados e, na inicialização, são lidos na memória para as operações restantes. Isso significa `master` que o banco de dados deve permanecer descriptografado. A chave real é gerenciada pela Microsoft. No entanto, os usuários com requisitos de segurança exigentes podem fornecer sua própria chave no Key Vault da mesma forma que é feito para o Azure Storage. O Key Vault fornece serviços como rotação de chaves e revogação.

A parte "transparente" do TDS vem do fato de que não há alterações de clientes necessárias para usar um banco de dados criptografado. Embora essa abordagem forneça uma boa segurança, vazar a senha do banco de dados é suficiente para que os usuários possam descriptografar os dados. Há outra abordagem que criptografa colunas ou tabelas individuais em um banco de dados. [Sempre criptografado](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) garante que em nenhum momento os dados criptografados aparecem em texto simples dentro do banco de dados.

Configurar esse nível de criptografia requer a execução de um assistente no SQL Server Management Studio para selecionar o tipo de criptografia e onde no Key Vault para armazenar as chaves associadas.

![Figura 10-6 Seleção de colunas em uma](./media/always-encrypted.png)
tabela a ser criptografada usando sempre a figura criptografada**10-6**. Selecionando colunas em uma tabela a ser criptografada usando Always Encrypted.

Os aplicativos clientes que leem informações dessas colunas criptografadas precisam fazer subsídios especiais para ler dados criptografados. As seqüências de `Column Encryption Setting=Enabled` conexão precisam ser atualizadas e as credenciais do cliente devem ser recuperadas do Key Vault. O cliente sql server deve então ser preparado com as chaves de criptografia da coluna. Feito isso, as demais ações usam as interfaces padrão para o SQL Client. Ou seja, ferramentas como Dapper e Entity Framework, que são construídas em cima do SQL Client, continuarão a funcionar sem alterações. O Always Encrypted pode ainda não estar disponível para todos os drivers do SQL Server em todos os idiomas.

A combinação de TDE e Always Encrypted, que podem ser usados com chaves específicas do cliente, garante que até mesmo os requisitos de criptografia mais exigentes sejam suportados.

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB é o mais novo banco de dados fornecido pela Microsoft no Azure. Foi construído do zero com a segurança e a criptografia em mente. A criptografia AES-256bit é padrão para todos os bancos de dados Cosmos DB e não pode ser desativada. Juntamente com o requisito TLS 1.2 para comunicação, toda a solução de armazenamento é criptografada.

![Figura 10-7 O fluxo de criptografia](./media/cosmos-encryption.png)
de dados dentro do Cosmos DB**Figura 10-7**. O fluxo de criptografia de dados dentro do Cosmos DB.

Embora o Cosmos DB não forneça chaves de criptografia ao cliente, houve um trabalho significativo feito pela equipe para garantir que ele permaneça em conformidade com o PCI-DSS sem isso. O Cosmos DB também não suporta nenhum tipo de criptografia de coluna única semelhante ao Always Encrypted do Azure SQL.

## <a name="keeping-secure"></a>Mantendo-se seguro

O Azure tem todas as ferramentas necessárias para lançar um produto altamente seguro. No entanto, uma cadeia é tão forte quanto seu elo mais fraco. Se os aplicativos implantados em cima do Azure não forem desenvolvidos com uma mentalidade de segurança adequada e boas auditorias de segurança, então eles se tornam o elo fraco da cadeia. Existem muitas grandes ferramentas de análise estática, bibliotecas de criptografia e práticas de segurança que podem ser usadas para garantir que o software instalado no Azure seja tão seguro quanto o próprio Azure. Exemplos incluem [ferramentas de análise estática,](https://www.whitesourcesoftware.com/) [bibliotecas de criptografia](https://www.libressl.org/)e práticas de [segurança.](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)

>[!div class="step-by-step"]
>[Próximo](security.md)
>[anterior](devops.md)
