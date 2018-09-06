---
title: Usando atividades procedurais
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804733"
---
# <a name="using-procedural-activities"></a><span data-ttu-id="7682f-102">Usando atividades procedurais</span><span class="sxs-lookup"><span data-stu-id="7682f-102">Using Procedural Activities</span></span>
<span data-ttu-id="7682f-103">O exemplo usa <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, e atividades de <xref:System.Activities.Statements.WriteLine> para implementar um jogo de estimativa.</span><span class="sxs-lookup"><span data-stu-id="7682f-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="7682f-104">O jogo de estimativa seleciona um número aleatório e o jogador tem que descobrir esse número.</span><span class="sxs-lookup"><span data-stu-id="7682f-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="7682f-105">Quando o jogador envia uma estimativa incorreta, o fluxo de trabalho fornece uma dica descobrir se maior ou menor.</span><span class="sxs-lookup"><span data-stu-id="7682f-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="7682f-106">Se o jogador suponha o número em menos de 7 tentativas, as parabéns especiais são exibidas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="7682f-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="7682f-107">Atividades personalizados nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="7682f-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="7682f-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="7682f-108">ReadLine</span></span>  
 <span data-ttu-id="7682f-109">Ler uma linha de texto de console.</span><span class="sxs-lookup"><span data-stu-id="7682f-109">Reads a line of text from the console.</span></span> <span data-ttu-id="7682f-110">Esta atividade deriva da classe de <xref:System.Activities.NativeActivity> e cria-se um indexador que é que o aplicativo de console quando uma linha é lido.</span><span class="sxs-lookup"><span data-stu-id="7682f-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="7682f-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="7682f-111">PromptInt</span></span>  
 <span data-ttu-id="7682f-112">Solicita ao usuário digite um número e depois lê de uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="7682f-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="7682f-113">A atividade deriva de <xref:System.Activities.Activity%601> e usa as atividades de <xref:System.Activities.Statements.WriteLine> e de `ReadLine` .</span><span class="sxs-lookup"><span data-stu-id="7682f-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="7682f-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="7682f-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="7682f-115">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de GuessingGame.sln.</span><span class="sxs-lookup"><span data-stu-id="7682f-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7682f-116">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="7682f-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7682f-117">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="7682f-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7682f-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7682f-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7682f-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7682f-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7682f-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7682f-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7682f-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7682f-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`