---
title: "A conexão de contexto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9a50f3d91f8de146aee602cc94a33728e5a4c738
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="the-context-connection"></a>A conexão de contexto
O problema de acesso a dados internos é um cenário bastante comum. Ou seja, você deseja acessar o mesmo servidor no qual o procedimento armazenado ou função CLR está sendo executado. Uma opção é criar uma conexão usando <xref:System.Data.SqlClient.SqlConnection>, especificar uma cadeia de conexão que aponta para o servidor local, e abrir a conexão. Isso exige a especificação de credenciais para fazer logon. A conexão está em uma sessão do banco de dados diferente do procedimento armazenado ou da função, pode ter opções diferentes de `SET`, pode estar em uma transação separada, não ver suas tabelas temporárias e assim por diante. Se seu código gerenciado do procedimento armazenado ou função está sendo executado no processo do SQL Server, é porque alguém se conectou a esse servidor e executou uma instrução SQL para chamá-lo. Você deseja provavelmente que o procedimento armazenado ou a função seja executada no contexto dessa conexão, junto com sua transação, opções `SET` e assim por diante. Isso é chamado de conexão de contexto.  
  
 A conexão de contexto permite executar instruções Transact-SQL no mesmo contexto em que seu código foi chamado pela primeira vez. Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1.  [A Conexão de contexto](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Consulte também  
 [Criando objetos do SQL Server 2005 em código gerenciado](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
