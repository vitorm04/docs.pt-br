---
title: LeiaMe para exemplo de autenticação de proteção estendida
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d45271180b7f00ba78d106f2a93d5860375da5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="readme-for-extended-protection-authentication-sample"></a>LeiaMe para exemplo de autenticação de proteção estendida
Proteção estendida é uma iniciativa de segurança para impedir ataques man-in-the-middle (MITM), em que um invasor (o "man-in-the-middle") intercepta as credenciais do cliente e as utiliza para acessar recursos protegidos no servidor pretendido do cliente.  
  
 Para obter mais informações, consulte [proteção estendida para visão geral da autenticação](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Este exemplo só funciona quando hospedados no IIS. Ele não funciona no servidor de desenvolvimento do Visual Studio porque que não oferece suporte a HTTPS.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1.  Instale o IIS no computador de adicionar ou remover programas -> recursos do Windows.  
  
2.  Ativar a autenticação do Windows em recursos do Windows: serviços de informações da Internet -> Serviços da World Wide Web -> Segurança -> autenticação do Windows.  
  
3.  Ativar a ativação HTTP nos recursos do Windows: Microsoft .NET Framework 3.5.1 -> Ativação HTTP do Windows Communication Foundation.  
  
4.  Este exemplo requer que o cliente estabelecer um canal seguro com o servidor e então exige a presença de um certificado de servidor que pode ser instalado do Gerenciador de serviços de informações da Internet (IIS).  
  
    1.  Abra o Gerenciador do IIS -> certificados do servidor (a partir da guia de exibição de recurso).  
  
    2.  Com a finalidade de testar este exemplo, você pode criar um certificado autoassinado. (Se você não quiser o Internet Explorer para solicitar que você sobre o certificado não está sendo seguro, você pode instalá-lo no repositório de autoridade de certificado de raiz confiável).  
  
5.  Vá para o painel de ações para o site da Web padrão. Clique em Editar Site -> associações. Adicione HTTPS como um tipo se ele não ainda estiver presente, com o número da porta 443 e atribui o certificado SSL criado na etapa anterior.  
  
6.  O serviço de compilação. Isso cria um diretório virtual no IIS para você (da ação de compilação post especificada nas propriedades do projeto) e copia os arquivos de dll,. svc e configuração conforme necessário para um serviço ser hospedado na Web.  
  
7.  Abra o Gerenciador do IIS. O diretório virtual (ExtendedProtection) que você criou na etapa anterior e selecione Converter em aplicativo.  
  
8.  Abra o módulo de autenticação no Gerenciador do IIS para este diretório virtual e habilite a autenticação do Windows.  
  
9. Abra o Advanced configurações de autenticação do Windows para este diretório virtual e defina-a como necessária, como, por exemplo, a configuração de ExtendedProtection correspondente é definida como Always.  
  
10. Você pode testar o serviço acessando a URL de uma janela do navegador. Se você quiser acessar essa URL de uma máquina cruzada, certifique-se de que o firewall está aberto todas as conexões de entrada HTTP e HTTPS.  
  
11. Abra o arquivo de configuração do cliente e forneça um nome de computador completo para o \<cliente >- \<ponto de extremidade >-atributo de endereço, substituindo << full_machine_name >>.  
  
12. Execute o cliente. O cliente se comunica com o serviço de estabelecer um canal seguro e usando proteção estendida nos bastidores.
