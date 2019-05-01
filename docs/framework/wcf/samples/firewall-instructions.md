---
title: Instruções do firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051925"
---
# <a name="firewall-instructions"></a>Instruções do firewall
Você deve habilitar várias portas ou programas no firewall para que os exemplos do Windows Communication Foundation (WCF) podem funcionar. Muitos dos exemplos de se comunicar por meio de portas no intervalo 8000-8003 e porta 9000. O firewall está ativado por padrão e impede o acesso a essas portas. Para habilitar o firewall para os exemplos, conclua um dos procedimentos a seguir, dependendo de suas necessidades e ambiente de segurança:  
  
- Opção 1: Habilite interativamente amostras durante a execução. Não fazer nenhuma alteração de avanço em sua configuração de firewall e prossiga para começar a criar e executar os exemplos. Quando um exemplo é executado, uma **o alerta de segurança do Windows** caixa de diálogo é exibida. O programa de exemplo em questão, em seguida, pode ser adicionado interativamente a uma lista desbloqueada. Com esse procedimento, você terá que reiniciar, em seguida, o exemplo.  
  
- Opção 2: Habilite programas de exemplo com antecedência. Iniciar o **painel de controle do Windows Firewall** miniaplicativo e habilitar o exemplo de programas que deseja executar. Portanto, os arquivos executáveis existirem, você deve criar os programas de primeiro. Você pode encontrar instruções mais detalhadas no procedimento a seguir.  
  
- Opção 3: Habilite um intervalo de portas com antecedência. Iniciar o **Firewall do Windows** **painel de controle** miniaplicativo e habilite as portas 80, 443, 8000 8003 e 9000, que são usados pelos exemplos. Você pode encontrar instruções mais detalhadas no procedimento a seguir. Essa opção é menos segura do que os outros porque ele permite que qualquer programa usam essas portas, não apenas os exemplos.  
  
 Se você não tiver certeza de qual procedimento para usar, escolha a primeira opção. Se você estiver executando um firewall de outro fornecedor, talvez você precise fazer alterações semelhantes.  
  
> [!IMPORTANT]
>  Alterar sua configuração de firewall afeta sua segurança. É recomendável que você registre as alterações que você fizer e removê-los quando tiver terminado de trabalhar com os exemplos.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Para habilitar programas de exemplos com antecedência  
  
1. Crie o exemplo.  
  
2. Clique em **inicie**, clique em **execute**e o tipo `firewall.cpl`. Isso abre o **painel de controle do Windows Firewall** miniaplicativo.  
  
    > [!NOTE]
    >  Você deve ter permissão para alterar as configurações de Firewall para executar os exemplos que exigem a capacidade de se comunicar através do Firewall do Windows. Se algumas configurações do firewall não estão disponíveis e o computador está conectado a um domínio, o administrador do sistema talvez esteja controlando essas configurações por meio de diretiva de grupo.  
  
3. Conclua uma das seguintes etapas específicas operacionais para permitir um programa pelo Firewall do Windows:  
  
    - No Windows 7 ou Windows Server 2008 r2, clique em **permitem que um programa ou recurso pelo Firewall do Windows**. Clique em **alterar configurações**, permitir **outro programa...** .  
  
    - Na [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], clique em **permitir um programa pelo Firewall do Windows**.  
  
4. Sobre o **exceções** , clique em **adicionar programa**.  
  
5. Clique o **procurar** botão e selecione o arquivo executável do exemplo que você pretende executar.  
  
6. Repita as etapas 4 e 5 até ter adicionado os arquivos executáveis de todos os exemplos que você pretende executar.  
  
7. Clique em **Okey** para fechar o miniaplicativo de firewall.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Para habilitar um intervalo de portas com antecedência  
  
1. Clique em **inicie**, clique em **execute**e o tipo `firewall.cpl`. Isso abre o **painel de controle do Windows Firewall** miniaplicativo.  
  
2. No Windows 7 ou Windows Server 2008 R2, siga estas etapas.  
  
    1. Clique em **configurações avançadas** na coluna esquerda da janela do Firewall do Windows.  
  
    2. Clique em **regras de entrada** na coluna à esquerda.  
  
    3. Clique em **novas regras** na coluna à direita.  
  
    4. Selecione **porta** e clique em **próxima**.  
  
    5. Selecione **TCP** e insira `8000, 8001, 8002, 8003, 9000, 80, 443` no **portas locais específicas** campo.  
  
    6. Clique em **Avançar**.  
  
    7. Selecione **permitir a conexão**e clique em **próxima** .  
  
    8. Selecione **domínio** e **privada**e clique em **próxima**.  
  
    9. Nomeie essa regra `WCF-WF 4.0 Samples`e clique em **concluir**.  
  
    10. Clique em **regras de saída** e repita as etapas de c para h.  
  
3. Na [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], siga estas etapas.  
  
    1. Clique em **permitir um programa pelo Firewall do Windows**.  
  
    2. Sobre o **exceções** , clique em **adicionar porta**.  
  
    3. Insira um nome, digite 8000 como o número da porta e selecione o **TCP** opção.  
  
    4. Clique o **Alterar escopo** botão, selecione o **minha rede** única opção de (sub-rede) e clique em **Okey**.  
  
    5. Repita as etapas de b a d para portas 8001, 8002, 8003, 9000, 80 e 443.  
  
4. Clique em **Okey** para fechar o miniaplicativo de firewall.  
  
> [!NOTE]
>  Remova todas as exceções de firewall quando tiver terminado de trabalhar com os exemplos. Para fazer isso, abra o **painel de controle do Windows Firewall** miniaplicativo e remove nenhum programa ou porta entradas que foram adicionadas por procedimentos anteriores.
