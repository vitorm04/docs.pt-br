---
title: "Como definir a cadeia de conexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7c17029dade53c724420fa5604ba3448ce6a6ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-define-the-connection-string"></a>Como definir a cadeia de conexão
Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual. Este tópico se baseia o [vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) modelo conceitual. O Modelo de Vendas do AdventureWorks é usado em todos os tópicos relacionados a tarefas na documentação do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Este tópico pressupõe que você já tenha configurado o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e definir o modelo de vendas do AdventureWorks. Para obter mais informações, consulte [como: definir manualmente os arquivos de modelo e mapeamento](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a). Os procedimentos neste tópico também estão incluídos no [como: configurar manualmente um projeto do Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Se você usar o assistente do [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] em um projeto do [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)], ele automaticamente gera um arquivo .edmx e configura o projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Para definir a cadeia de conexão do Entity Framework  
  
-   Abra o arquivo de configuração do aplicativo de projeto (app.config) e adicione a seguinte cadeia de conexão:  
  
  
  
     Se seu projeto não tem um arquivo de configuração do aplicativo, você pode adicionar uma selecionando **Adicionar Novo Item** do **projeto** menu, selecionando o **geral** categoria, selecionando **arquivo de configuração do aplicativo**e, em seguida, clicando em **adicionar**.  
  
## <a name="see-also"></a>Consulte também  
 [Quickstart](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675) (Início rápido)  
 [Como: criar um novo arquivo. edmx](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)
