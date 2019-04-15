---
title: 'Como: Gravar informações de evento em um arquivo de texto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: e696ccb7327197c2f3a2468d30085dc6d390e034
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312703"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="92f54-102">Como: Gravar informações de evento em um arquivo de texto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f54-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="92f54-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92f54-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="92f54-104">Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="92f54-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="92f54-105">Para adicionar e configurar o ouvinte de log de arquivo</span><span class="sxs-lookup"><span data-stu-id="92f54-105">To add and configure the file log listener</span></span>  
  
1. <span data-ttu-id="92f54-106">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="92f54-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="92f54-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="92f54-107">\- or -</span></span>  
  
     <span data-ttu-id="92f54-108">Se não houver nenhum arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="92f54-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="92f54-109">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="92f54-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="92f54-110">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="92f54-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="92f54-111">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="92f54-111">Click **Add**.</span></span>  
  
2. <span data-ttu-id="92f54-112">Localize a seção `<listeners>` no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92f54-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="92f54-113">Você localizará a seção \<listeners> na seção \<source> com o atributo de nome "DefaultSource", aninhado na seção \<system.diagnostics>, aninhada na seção \<configuration> superior.</span><span class="sxs-lookup"><span data-stu-id="92f54-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3. <span data-ttu-id="92f54-114">Adicione esse elemento a essa seção `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="92f54-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. <span data-ttu-id="92f54-115">Localize a seção `<sharedListeners>` na seção `<system.diagnostics>`, aninhada na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="92f54-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="92f54-116">Adicione esse elemento a essa seção `<sharedListeners>`:</span><span class="sxs-lookup"><span data-stu-id="92f54-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="92f54-117">Altere o valor do atributo `customlocation` para o diretório de log.</span><span class="sxs-lookup"><span data-stu-id="92f54-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92f54-118">Para definir o valor de uma propriedade ouvinte, use um atributo com o mesmo nome da propriedade, com todas as letras do nome em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="92f54-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="92f54-119">Por exemplo, os atributos `location` e `customlocation` definem os valores das propriedades <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> e <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.</span><span class="sxs-lookup"><span data-stu-id="92f54-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="92f54-120">Para gravar informações de evento no log de arquivos</span><span class="sxs-lookup"><span data-stu-id="92f54-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="92f54-121">Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações no log de arquivos.</span><span class="sxs-lookup"><span data-stu-id="92f54-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="92f54-122">Para obter mais informações, confira [Como: Gravar mensagens de Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como: Registrar exceções em log](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="92f54-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="92f54-123">Depois de configurar o ouvinte de log de arquivos para um assembly, ele receberá todas as mensagens que `My.Application.Log` grava desse assembly.</span><span class="sxs-lookup"><span data-stu-id="92f54-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f54-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92f54-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="92f54-125">Trabalhar com logs do aplicativo</span><span class="sxs-lookup"><span data-stu-id="92f54-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="92f54-126">Como: registrar exceções em log</span><span class="sxs-lookup"><span data-stu-id="92f54-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
