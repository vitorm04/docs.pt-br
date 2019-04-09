---
title: A conexão de contexto
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: f942bf6a8df034ee96b595a791a07e64bc2ec179
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195352"
---
# <a name="the-context-connection"></a>A conexão de contexto
O problema de acesso a dados internos é um cenário bastante comum. Ou seja, você deseja acessar o mesmo servidor no qual o procedimento armazenado ou função CLR está sendo executado. Uma opção é criar uma conexão usando <xref:System.Data.SqlClient.SqlConnection>, especificar uma cadeia de conexão que aponta para o servidor local, e abrir a conexão. Isso exige a especificação de credenciais para fazer logon. A conexão está em uma sessão do banco de dados diferente do procedimento armazenado ou da função, pode ter opções diferentes de `SET`, pode estar em uma transação separada, não ver suas tabelas temporárias e assim por diante. Se seu código gerenciado do procedimento armazenado ou função está sendo executado no processo do SQL Server, é porque alguém se conectou a esse servidor e executou uma instrução SQL para chamá-lo. Você deseja provavelmente que o procedimento armazenado ou a função seja executada no contexto dessa conexão, junto com sua transação, opções `SET` e assim por diante. Isso é chamado de conexão de contexto.  
  
 A conexão de contexto permite executar instruções Transact-SQL no mesmo contexto em que seu código foi chamado pela primeira vez. Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **Manuais Online do SQL Server**  
  
1.  [A conexão de contexto](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Consulte também

- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
