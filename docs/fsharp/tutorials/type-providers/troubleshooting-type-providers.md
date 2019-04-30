---
title: Solução de problemas de provedores de tipos
description: Descobrir as possíveis soluções para problemas que você têm maior probabilidade de encontrar ao usar provedores em, digite F#.
ms.date: 05/16/2016
ms.openlocfilehash: 6c675720e0b7c306a2916c94d8096d2f09c0daca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968214"
---
# <a name="troubleshooting-type-providers"></a>Solução de problemas de provedores de tipos

Este tópico descreve e fornece possíveis soluções para problemas que você têm maior probabilidade de encontrar ao usar provedores de tipos.

## <a name="possible-problems-with-type-providers"></a>Possíveis problemas com provedores de tipos

Se você encontrar um problema quando você trabalha com provedores de tipos, você pode examinar a tabela a seguir para as soluções mais comuns.

|Problema|Ações sugeridas|
|-------|-----------------|
|**Alterações de esquema**. Digite provedores funcionam melhor quando o esquema de fonte de dados é estável. Se você adiciona uma coluna ou tabela de dados ou fazer outra alteração nesse esquema, o provedor de tipos não reconhece automaticamente essas alterações.|Limpe ou recrie o projeto. Para limpar o projeto, escolha **construir**, **Clean** *ProjectName* na barra de menus. Para recompilar o projeto, escolha **construir**, **recompilar** *ProjectName* na barra de menus. Essas ações redefinir estado de todos os tipos de provedor e forçar o provedor para reconectar-se à fonte de dados e obter informações de esquema atualizado.|
|**Falha de Conexão**. A cadeia de caracteres de URL ou a conexão está incorreta, a rede estiver inoperante ou a fonte de dados ou o serviço não está disponível.|Para um serviço web ou um serviço OData, você pode tentar a URL no Internet Explorer para verificar se a URL está correta e se o serviço está disponível. Uma cadeia de caracteres de conexão do banco de dados, você pode usar as ferramentas de conexão de dados do **Gerenciador de servidores** para verificar se a cadeia de conexão é válida e o banco de dados está disponível. Depois de restaurar a conexão, você deve, em seguida, limpar ou recompilar o projeto para que o provedor de tipo serão reconectados à rede.|
|**Não é válidas credenciais**. Você deve ter permissões válidas para o serviço web ou de código-fonte de dados.|Para uma conexão de SQL, o nome de usuário e a senha que são especificados no arquivo de configuração ou de cadeia de caracteres de conexão devem ser válidos para o banco de dados. Se você estiver usando autenticação do Windows, você deve ter acesso ao banco de dados. O administrador de banco de dados pode identificar quais permissões para que necessárias acessem cada banco de dados e cada elemento dentro de um banco de dados.<br /><br />Para um serviço web ou um serviço de dados, você deve ter as credenciais apropriadas. A maioria dos provedores de tipo fornecem um objeto DataContext, que contém uma propriedade de credenciais que podem ser definidas com o nome de usuário apropriado e a chave de acesso.|
|**O caminho não é válido**. Um caminho para um arquivo não era válido.|Verifique se o caminho está correto e se o arquivo existe. Além disso, você deve colocar entre aspas qualquer backlashes no caminho adequadamente ou usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.|

## <a name="see-also"></a>Consulte também

- [Provedores de Tipos](index.md)