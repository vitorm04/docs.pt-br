---
title: 'Como: substituir a reserva de URL do WCF com uma reserva restrita'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: f9cfda1d4ca14dd380dd01f944d4c900f9832096
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307555"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Como: substituir a reserva de URL do WCF com uma reserva restrita
Uma reserva de URL permite que você restrinja quem pode receber mensagens de uma URL ou um conjunto de URLs. Uma reserva consiste em um modelo de URL, uma lista de controle de acesso (ACL) e um conjunto de sinalizadores. O modelo de URL define as URLs que afeta a reserva. Para obter mais informações sobre como os modelos de URL são processados, consulte [roteamento de solicitações de entrada](https://go.microsoft.com/fwlink/?LinkId=136764). A ACL controla qual usuário ou grupo de usuários tem permissão para receber mensagens das URLs especificadas. Os sinalizadores indicam se a reserva é conceder uma permissão de usuário ou grupo para escutar a URL diretamente ou para a permissão para escutar a algum outro processo.  
  
 Como parte da configuração padrão do sistema operacional, o Windows Communication Foundation (WCF) cria uma reserva e acessível globalmente para a porta 80 para habilitar todos os usuários executem aplicativos que usam uma associação HTTP dupla para comunicação duplex. Como a ACL nessa reserva é para todos, os administradores explicitamente não podem permitir ou impedir o permissão para escutar em uma URL ou um conjunto de URLs. Este tópico explica como excluir essa reserva e como recriar a reserva com uma ACL restrita.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)] você pode exibir todas as reservas de URL HTTP em um prompt de comando elevado, digitando `netsh http show urlacl`.  O exemplo a seguir mostra o que deve ser semelhante uma reserva de URL do WCF.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 A reserva consiste em um modelo de URL usado quando um aplicativo WCF está usando uma associação de duplo de HTTP para comunicação duplex. URLs desse formulário são usadas para um serviço WCF para enviar mensagens de volta para o cliente WCF ao se comunicar por uma associação de HTTP dupla. Todos tem permissão para escutar na URL, mas não para delegar a escuta para outro processo. Por fim, a ACL é descrita na segurança descritor SSDL (Definition Language). Para obter mais informações sobre o SSDL, consulte [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Para excluir a reserva de URL do WCF  
  
1. Clique em **inicie**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2. Digite **netsh http excluir urlacl url =http://+:80/Temporary_Listen_Addresses/**  na janela do prompt de comando.  
  
3. Se a reserva for excluída com êxito, a seguinte mensagem é exibida. **Reserva de URL excluída com êxito**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Criando um novo grupo de segurança e a nova reserva de URL restrito  
 Para substituir a reserva de URL do WCF com uma reserva restrita, você primeiro deve criar um novo grupo de segurança. Você pode fazer isso de duas maneiras: em um prompt de comando ou do console de gerenciamento do computador. Você só precisa fazer uma.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Para criar um novo grupo de segurança em um prompt de comando  
  
1. Clique em **inicie**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2. Digite **net localgroup "\<nome do grupo de segurança >" / comentário: "\<descrição do grupo de segurança >" / adicionar** no prompt de comando. Substituindo  **\<nome do grupo de segurança >** com o nome do grupo de segurança que você deseja criar e  **\<descrição do grupo de segurança >** com uma descrição adequada para o grupo de segurança.  
  
3. Se o grupo de segurança for criado com êxito, a seguinte mensagem é exibida. **O comando foi concluído com êxito.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Para criar um novo grupo de segurança do console de gerenciamento do computador  
  
1. Clique em **inicie**, clique em **painel de controle**, clique em **ferramentas administrativas**e clique em **gerenciamento de computador** para abrir o backup do computador Console de gerenciamento. Clique em **continuar** na janela controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2. Clique em **ferramentas do sistema**, clique em **usuários e grupos locais**, clique com botão direito **grupos** pasta e clique em **grupo novo** no menu de contexto que surge. Tipo no desejado **nome do grupo**, **descrição** e outros detalhes deste novo grupo de segurança e clique no **criar** botão para criar o grupo de segurança.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Para criar a reserva de URL restrita  
  
1. Clique em **inicie**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2. Digite **netsh http adicionar url urlacl =http://+:80/Temporary_Listen_Addresses/ usuário = "\<nome do computador >\\< nome do grupo de segurança\>**  no prompt de comando. Substituindo  **\<nome da máquina >** com o nome do computador no qual o grupo deve ser criado e  **\<nome do grupo de segurança >** com o nome do grupo de segurança que você criou anteriormente.  
  
3. Se a reserva é criada com êxito, a seguinte mensagem será exibida. **Reserva de URL adicionada com êxito**.
