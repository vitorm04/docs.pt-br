---
title: Solução de problemas de provedores de tipos
description: 'Descobrir possíveis soluções para problemas que você têm mais probabilidade de encontrar ao usar provedores de tipos em F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6dcae0e510d27fb0b07799b4edfe2d5bb9aeb2d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-type-providers"></a>Solução de problemas de provedores de tipos

Este tópico descreve e fornece possíveis soluções para problemas que você têm mais probabilidade de encontrar ao usar provedores de tipos.


## <a name="possible-problems-with-type-providers"></a>Possíveis problemas com provedores de tipos
Se você encontrar um problema quando você trabalha com provedores de tipos, você pode examinar a tabela a seguir para as soluções mais comuns.



|Problema|Ações sugeridas|
|-------|-----------------|
|**Alterações de esquema**. Digite provedores funcionam melhor quando o esquema de fonte de dados é estável. Se você adiciona uma coluna ou tabela de dados ou fazer outra alteração de esquema, o provedor de tipos não reconhece automaticamente essas alterações.|Limpar ou recompile o projeto. Para limpar o projeto, escolha **criar**, **limpar** *ProjectName* na barra de menus. Para recompilar o projeto, escolha **criar**, **recriar** *ProjectName* na barra de menus. Essas ações redefinir estado de todos os tipos de provedor e forçar o provedor para reconectar-se à fonte de dados e obter informações de esquema atualizado.|
|**Falha de Conexão**. A cadeia de caracteres de conexão ou de URL está incorreta, a rede está inoperante ou a fonte de dados ou o serviço não está disponível.|Para um serviço da web ou serviço OData, você pode tentar a URL no Internet Explorer para verificar se a URL está correta e se o serviço está disponível. Uma cadeia de caracteres de conexão do banco de dados, você pode usar as ferramentas de conexão de dados no **Server Explorer** para verificar se a cadeia de conexão é válida e o banco de dados está disponível. Depois de restaurar a conexão, você deve limpar ou recompile o projeto para que o provedor de tipo será reconectar-se à rede.|
|**Não é válidas credenciais**. Você deve ter permissões válidas para o serviço web ou de fonte de dados.|Para uma conexão de SQL, o nome de usuário e a senha que são especificadas no arquivo de configuração ou de cadeia de caracteres de conexão devem ser válidos para o banco de dados. Se você estiver usando autenticação do Windows, você deve ter acesso ao banco de dados. O administrador de banco de dados pode identificar quais permissões para que necessárias acessem cada banco de dados e cada elemento em um banco de dados.<br /><br />Para um serviço web ou um serviço de dados, você deve ter as credenciais apropriadas. A maioria dos provedores de tipo fornecem um objeto de DataContext, que contém uma propriedade de credenciais que podem ser definidas com o nome de usuário apropriado e a chave de acesso.|
|**Caminho inválido**. Um caminho para um arquivo não era válido.|Verifique se o caminho está correto e se o arquivo existe. Além disso, você deve colocar entre aspas qualquer backlashes no caminho adequadamente ou usar uma cadeia de caracteres textual ou cadeia de caracteres entre aspas triplas.|

## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)
