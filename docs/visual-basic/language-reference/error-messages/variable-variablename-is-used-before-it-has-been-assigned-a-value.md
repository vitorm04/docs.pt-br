---
title: A variável '<variablename>' é usada antes de receber um valor
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 6db8626701267f2051b289b267e7b2d9da51c283
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162213"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="d1d04-102">BC42104: a variável ' \<variablename> ' é usada antes de receber um valor</span><span class="sxs-lookup"><span data-stu-id="d1d04-102">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="d1d04-103">A variável ' \<variablename> ' é usada antes de receber um valor.</span><span class="sxs-lookup"><span data-stu-id="d1d04-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="d1d04-104">Uma exceção de referência nula pode resultar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d1d04-104">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="d1d04-105">Um aplicativo tem pelo menos um caminho possível por meio de seu código que lê uma variável antes que qualquer valor seja atribuído a ela.</span><span class="sxs-lookup"><span data-stu-id="d1d04-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="d1d04-106">Se uma variável nunca tiver sido atribuído um valor, ela manterá o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d1d04-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="d1d04-107">Para um tipo de dados de referência, esse valor padrão é [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d1d04-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="d1d04-108">A leitura de uma variável de referência que tem um valor de `Nothing` pode causar um <xref:System.NullReferenceException> em algumas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="d1d04-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="d1d04-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d1d04-109">By default, this message is a warning.</span></span> <span data-ttu-id="d1d04-110">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d1d04-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="d1d04-111">**ID do erro:** BC42104</span><span class="sxs-lookup"><span data-stu-id="d1d04-111">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d1d04-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d1d04-112">To correct this error</span></span>

- <span data-ttu-id="d1d04-113">Verifique sua lógica de fluxo de controle e certifique-se de que a variável tem um valor válido antes que o controle passe para qualquer instrução que a Leia.</span><span class="sxs-lookup"><span data-stu-id="d1d04-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="d1d04-114">Uma maneira de garantir que a variável sempre tenha um valor válido é inicializá-la como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="d1d04-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="d1d04-115">Consulte "inicialização" na [instrução Dim](../statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d1d04-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1d04-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="d1d04-116">See also</span></span>

- [<span data-ttu-id="d1d04-117">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="d1d04-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="d1d04-118">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="d1d04-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="d1d04-119">Solução de problemas de Variáveis</span><span class="sxs-lookup"><span data-stu-id="d1d04-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
