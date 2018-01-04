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
# <a name="activity-localization"></a><span data-ttu-id="f4682-102">Localização de atividades</span><span class="sxs-lookup"><span data-stu-id="f4682-102">Activity Localization</span></span>
<span data-ttu-id="f4682-103">Quando os aplicativos de fluxo de trabalho e componentes têm o potencialmente ser localizado em outros idiomas e culturas, as cadeias de caracteres de recursos devem ser usadas de modo que eles possam ser encontradas sem recompilar.</span><span class="sxs-lookup"><span data-stu-id="f4682-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="f4682-104">Localização de atividades</span><span class="sxs-lookup"><span data-stu-id="f4682-104">Activity Localization</span></span>  
 <span data-ttu-id="f4682-105">Como com todos os aplicativos que devem ser localizados (liberado em versões diferentes para diferentes idiomas e culturas), nenhuma cadeias de caracteres que são exibidas ao usuário não devem ser colocadas diretamente no código, mas em vez de ser armazenadas em um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f4682-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="f4682-106">As cadeias de caracteres, em seguida, podem ser acessadas por meio de <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span><span class="sxs-lookup"><span data-stu-id="f4682-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="f4682-107">Se você estiver desenvolvendo um componente que é distribuído em vários idiomas, você também deseja usar também cadeias de caracteres de recurso para mensagens de validação de atividade, dados definidos pelo usuário de rastreamento, mensagens de rastreamento, e mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="f4682-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="f4682-108">O exercício seguir demonstra como usar um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f4682-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="f4682-109">Utilizando arquivos de recurso para cadeias de caracteres encontradas</span><span class="sxs-lookup"><span data-stu-id="f4682-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="f4682-110">Em [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], com o botão direito no projeto **Solution Explorer** e selecione **adicionar...** , **Novo Item...** .</span><span class="sxs-lookup"><span data-stu-id="f4682-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="f4682-111">Selecione **arquivo de recursos** e nomeie o arquivo ErrorResources.resx.</span><span class="sxs-lookup"><span data-stu-id="f4682-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="f4682-112">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f4682-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="f4682-113">Abra o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f4682-113">Open the resource file.</span></span> <span data-ttu-id="f4682-114">Adicionar uma nova entrada com um **nome** de ErrorString e um **valor** de "a atividade não é válida."</span><span class="sxs-lookup"><span data-stu-id="f4682-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="f4682-115">Adicione as instruções de `using` a sua classe.</span><span class="sxs-lookup"><span data-stu-id="f4682-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="f4682-116">Crie um recurso em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f4682-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="f4682-117">Obter a cadeia de caracteres o gerenciador de recursos onde se necessário.</span><span class="sxs-lookup"><span data-stu-id="f4682-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="f4682-118">O exemplo de código a seguir demonstra como utilizar cadeias de caracteres encontradas no método de <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="f4682-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
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
