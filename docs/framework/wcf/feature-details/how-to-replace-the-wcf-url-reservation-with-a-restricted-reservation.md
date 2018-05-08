---
title: 'How to: Replace the WCF URL Reservation with a Restricted Reservation'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 823a59f53823a2480655c4f8720504dd4199d0bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>How to: Replace the WCF URL Reservation with a Restricted Reservation
Uma reserva de URL permite restringir quem pode receber mensagens de uma URL ou um conjunto de URLs. Uma reserva consiste em um modelo de URL, uma lista de controle de acesso (ACL) e um conjunto de sinalizadores. O modelo de URL define qual afeta a reserva de URLs. Para obter mais informações sobre como os modelos de URL são processados, consulte [roteamento de solicitações de entrada](http://go.microsoft.com/fwlink/?LinkId=136764). A ACL controla qual usuário ou grupo de usuários tem permissão para receber mensagens das URLs especificadas. Os sinalizadores indicam se a reserva é para conceder uma permissão de usuário ou grupo para escutar a URL diretamente ou a permissão para escutar algum outro processo.  
  
 Como parte da configuração do sistema operacional padrão, o Windows Communication Foundation (WCF) cria uma reserva globalmente acessível para a porta 80 para habilitar todos os usuários executem aplicativos que usam uma associação HTTP dupla para comunicação duplex. Como a ACL nessa reserva é para todos, os administradores explicitamente não podem permitir ou impedir permissão para escutar em uma URL ou um conjunto de URLs. Este tópico explica como excluir essa reserva e como recriar a reserva com uma ACL restrita.  
  
 Em [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)] você pode exibir todas as reservas de URL de HTTP em um prompt de comando com privilégios elevados, digitando `netsh http show urlacl`.  O exemplo a seguir mostra o que deve se assemelhar uma reserva de URL do WCF.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 A reserva consiste em um modelo de URL usado quando um aplicativo WCF está usando uma associação de dupla de HTTP para comunicação duplex. URLs deste formulário são usadas para um serviço WCF para enviar mensagens de volta para o cliente do WCF ao se comunicar por uma associação de dupla de HTTP. Todos tem permissão para escutar na URL, mas não para delegar a escuta de outro processo. Por fim, a ACL é descrita em segurança descritor SSDL (Definition Language). Para obter mais informações sobre o SSDL, consulte [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Para excluir a reserva de URL do WCF  
  
1.  Clique em **iniciar**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela de controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2.  Digite **netsh http excluir url urlacl =http://+:80/Temporary_Listen_Addresses/**  na janela do prompt de comando.  
  
3.  Se a reserva é excluída com êxito, a seguinte mensagem será exibida. **Reserva de URL excluída com êxito**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Criar um novo grupo de segurança e nova reserva de URL restrito  
 Para substituir a reserva de URL do WCF com uma reserva restrita, crie primeiro um novo grupo de segurança. Você pode fazer isso de duas maneiras: em um prompt de comando ou do console de gerenciamento do computador. Você tem apenas um.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Para criar um novo grupo de segurança em um prompt de comando  
  
1.  Clique em **iniciar**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela de controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2.  Digite **net localgroup "\<nome do grupo de segurança >" /Comment: "\<descrição do grupo de segurança >" /Add** no prompt de comando. Substituindo  **\<nome do grupo de segurança >** com o nome do grupo de segurança que você deseja criar e  **\<descrição do grupo de segurança >** com uma descrição adequada para o grupo de segurança.  
  
3.  Se o grupo de segurança é criado com êxito, a seguinte mensagem é exibida. **O comando foi concluído com êxito.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Para criar um novo grupo de segurança do console de gerenciamento do computador  
  
1.  Clique em **iniciar**, clique em **painel de controle**, clique em **ferramentas administrativas**e clique em **gerenciamento do computador** para abrir o computador Console de gerenciamento. Clique em **continuar** na janela de controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2.  Clique em **ferramentas do sistema**, clique em **usuários e grupos locais**, clique com botão direito **grupos** pasta e clique em **novo grupo** no menu de contexto que aparece. Tipo no desejado **nome do grupo**, **descrição** e outros detalhes deste novo grupo de segurança e clique no **criar** botão para criar o grupo de segurança.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Para criar a reserva de URL restrita  
  
1.  Clique em **iniciar**, aponte para **todos os programas**, clique em **Acessórios**, clique com botão direito **Prompt de comando** e clique em **executar como Administrador** no menu de contexto que aparece. Clique em **continuar** na janela de controle de conta de usuário (UAC) que pode solicitar permissões para continuar.  
  
2.  Digite **netsh http adicionar url urlacl =http://+:80/Temporary_Listen_Addresses/ usuário = "\<nome do computador >\\< nome do grupo de segurança\>**  no prompt de comando. Substituindo  **\<nome do computador >** com o nome do computador no qual o grupo deve ser criado e  **\<nome do grupo de segurança >** com o nome do grupo de segurança que você criou anteriormente.  
  
3.  Se a reserva for criada com êxito, a seguinte mensagem é exibida. **Reserva de URL adicionada com êxito**.
