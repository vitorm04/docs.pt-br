---
title: "Ocorreram erros na compilação dos esquemas XML no projeto"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords: BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Ocorreram erros na compilação dos esquemas XML no projeto
Ocorreram erros ao compilar os esquemas XML no projeto. Por isso, o XML IntelliSense não está disponível.  
  
 Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto. Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) XSD que está em conflito com o esquema XSD existente definido para o projeto.  
  
 **ID do erro:** BC36810  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Clique duas vezes no aviso no **lista erros** janela. Visual Basic levará você para o local no arquivo XSD que é a origem do aviso. Corrija o erro no esquema XSD.  
  
-   Garantir que todos os arquivos de esquema (. xsd) XSD são incluídos no projeto. Talvez você precise clicar em **Mostrar todos os arquivos** no **projeto** para ver seu. xsd arquivos em **Gerenciador de soluções**. Clique em um arquivo. xsd e, em seguida, clique em **incluir no projeto** para incluir o arquivo no seu projeto.  
  
-   Se você estiver usando o Assistente de esquema XML, esse erro pode ocorrer se inferir esquemas mais de uma vez da mesma fonte. Nesse caso, você pode remover os arquivos existentes do esquema XSD do projeto, adicione um novo XML para o modelo de item de esquema e, em seguida, forneça o XML ao Assistente de esquema com todas as fontes de XML aplicável para o seu projeto.  
  
-   Se nenhum erro for identificado no seu esquema XSD, o compilador XML pode não ter informações suficientes para fornecer uma mensagem de erro detalhada. Você poderá obter informações mais detalhadas de erro se você garantir que os namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam a namespaces XML identificados para o esquema XML definido no Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Janela Lista de Erros](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
