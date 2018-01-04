---
title: "Localização de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccabcda9e26751db80ee7e955458d0eee0cae7e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-localization"></a>Localização de atividades
Quando os aplicativos de fluxo de trabalho e componentes têm o potencialmente ser localizado em outros idiomas e culturas, as cadeias de caracteres de recursos devem ser usadas de modo que eles possam ser encontradas sem recompilar.  
  
## <a name="activity-localization"></a>Localização de atividades  
 Como com todos os aplicativos que devem ser localizados (liberado em versões diferentes para diferentes idiomas e culturas), nenhuma cadeias de caracteres que são exibidas ao usuário não devem ser colocadas diretamente no código, mas em vez de ser armazenadas em um arquivo de recurso. As cadeias de caracteres, em seguida, podem ser acessadas por meio de <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`. Se você estiver desenvolvendo um componente que é distribuído em vários idiomas, você também deseja usar também cadeias de caracteres de recurso para mensagens de validação de atividade, dados definidos pelo usuário de rastreamento, mensagens de rastreamento, e mensagens de erro.  
  
 O exercício seguir demonstra como usar um arquivo de recurso.  
  
#### <a name="using-resource-files-for-localized-strings"></a>Utilizando arquivos de recurso para cadeias de caracteres encontradas  
  
1.  Em [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], com o botão direito no projeto **Solution Explorer** e selecione **adicionar...** , **Novo Item...** .  
  
2.  Selecione **arquivo de recursos** e nomeie o arquivo ErrorResources.resx. Clique em **Adicionar**.  
  
3.  Abra o arquivo de recurso. Adicionar uma nova entrada com um **nome** de ErrorString e um **valor** de "a atividade não é válida."  
  
4.  Adicione as instruções de `using` a sua classe.  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  Crie um recurso em seu projeto.  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  Obter a cadeia de caracteres o gerenciador de recursos onde se necessário.  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 O exemplo de código a seguir demonstra como utilizar cadeias de caracteres encontradas no método de <xref:System.Activities.Activity.CacheMetadata%2A> .  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
