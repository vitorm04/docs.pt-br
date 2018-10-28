---
title: LeiaMe para exemplo de autenticação de proteção estendida
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 19fe961e346874346485442bd0ba90badab5f79f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192467"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>LeiaMe para exemplo de autenticação de proteção estendida
Proteção estendida é uma iniciativa de segurança para proteger contra ataques (MITM) de man-in-the-middle, em que um invasor (o "man-in-the-middle") intercepta as credenciais de um cliente e os utiliza para acessar recursos protegidos no servidor pretendido do cliente.  
  
 Para obter mais informações, consulte [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Este exemplo só funciona quando hospedado no IIS. Ele não funciona no Visual Studio Development Server porque o que não dá suporte a HTTPS.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1.  Instalar o IIS no computador, de adicionar ou remover programas -> recursos do Windows.  
  
2.  Ativar a autenticação do Windows nos recursos do Windows: serviços de informações da Internet -> Serviços da World Wide Web -> Segurança -> autenticação do Windows.  
  
3.  Ativar a ativação HTTP nos recursos do Windows: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.  
  
4.  Este exemplo requer que o cliente estabelecer um canal seguro com o servidor e, assim, ele exige a presença de um certificado de servidor que pode ser instalado do Gerenciador de serviços de informações da Internet (IIS).  
  
    1.  Abra o Gerenciador do IIS -> certificados de servidor (da guia de exibição de recurso).  
  
    2.  Para fins de teste neste exemplo, você pode criar um certificado autoassinado. (Se você não quiser o Internet Explorer para avisá-lo sobre o certificado não ser seguro, você pode instalá-lo no repositório raiz confiável do certificado da autoridade).  
  
5.  Vá para o painel de ações para o site da Web padrão. Clique em Editar Site -> associações. Adicione HTTPS como um tipo se ele não ainda estiver presente, com o número da porta 443 e atribuir o certificado SSL criado na etapa anterior.  
  
6.  Crie o serviço. Isso cria um diretório virtual no IIS para você (da ação de compilação de post especificada nas propriedades do projeto) e copia os arquivos dll,. svc e configuração conforme necessário para um serviço seja hospedado na Web.  
  
7.  Abra o Gerenciador do IIS. O diretório virtual (ExtendedProtection) que você criou na etapa anterior com o botão direito e selecionar Converter em aplicativo.  
  
8.  Abra o módulo de autenticação no Gerenciador do IIS para este diretório virtual e habilitar a autenticação do Windows.  
  
9. Abra as configurações para Windows autenticação avançada para este diretório virtual e defina-a como necessária, já que, no exemplo, a configuração de ExtendedProtection correspondente é definida como Always.  
  
10. Você pode testar o serviço acessando a URL de uma janela do navegador. Se você quiser acessar essa URL em uma máquina cruzada, certifique-se de que o firewall está aberto, todas as conexões de entrada HTTP e HTTPS.  
  
11. Abra o arquivo de configuração do cliente e forneça um nome de computador completo para o \<cliente >- \<ponto de extremidade >-atributo de endereço, substituindo << full_machine_name >>.  
  
12. Execute o cliente. O cliente se comunica com o serviço estabelecendo um canal seguro e usar a proteção estendida nos bastidores.
