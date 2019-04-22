---
title: Ocorreram erros na compilação dos esquemas XML no projeto
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842519"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Ocorreram erros na compilação dos esquemas XML no projeto
Ocorreram erros ao compilar os esquemas XML no projeto. Por isso, o XML IntelliSense não está disponível.  
  
 Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto. Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) de XSD que está em conflito com o esquema XSD existente definido para o projeto.  
  
 **ID do erro:** BC36810  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Clique duas vezes no aviso na **lista de erros** janela. Visual Basic levará você até o local no arquivo XSD que é a origem do aviso. Corrija o erro no esquema XSD.  
  
-   Garanta que todos os arquivos de esquema (. xsd) de XSD são incluídos no projeto. Você talvez precise clicar **Show All Files** na **projeto** menu para ver seu. xsd de arquivos no **Gerenciador de soluções**. Um arquivo. xsd com o botão direito e, em seguida, clique em **Include In Project** para incluir o arquivo em seu projeto.  
  
-   Se você estiver usando o Assistente de XML para esquema, esse erro pode ocorrer se você inferir esquemas mais de uma vez da mesma fonte. Nesse caso, você pode remover os arquivos de esquema XSD existentes do projeto, adicione um novo XML ao modelo de item de esquema e, em seguida, forneça o XML para o Assistente de esquema com todas as fontes XML aplicáveis para seu projeto.  
  
-   Se nenhum erro for identificado no esquema XSD, o compilador XML não pode ter informações suficientes para fornecer uma mensagem de erro detalhada. Você poderá obter informações mais detalhadas de erro se você garantir que os namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam os namespaces XML identificados para o esquema XML definido no Visual Studio.  
  
## <a name="see-also"></a>Consulte também

- [Janela Lista de Erros](/visualstudio/ide/reference/error-list-window)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
