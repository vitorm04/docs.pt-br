---
title: Foi criada uma referência para o assembly de interoperabilidade inserido '<assembly1>' devido a uma referência indireta a esse assembly a partir do assembly '<assembly2>'
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: c0b4f56e3d1613486dd1198976557831ce657e1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774850"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a><span data-ttu-id="874ae-102">Foi criada uma referência ao assembly de interoperabilidade inserido '\<assembly1 >' devido a uma referência indireta ao assembly do assembly '\<assembly2 >'</span><span class="sxs-lookup"><span data-stu-id="874ae-102">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'</span></span>
<span data-ttu-id="874ae-103">Foi criada uma referência para o assembly de interoperabilidade inserido '\<assembly1>' devido a uma referência indireta a esse assembly do assembly '\<assembly2>'.</span><span class="sxs-lookup"><span data-stu-id="874ae-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="874ae-104">Considere alterar a propriedade 'Inserir Tipos de Interoperabilidade' em um dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="874ae-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="874ae-105">Você adicionou uma referência a um assembly (assembly1) que tem a propriedade `Embed Interop Types` definida como `True`.</span><span class="sxs-lookup"><span data-stu-id="874ae-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="874ae-106">Isso instrui o compilador a inserir informações de tipo de interoperabilidade desse assembly.</span><span class="sxs-lookup"><span data-stu-id="874ae-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="874ae-107">No entanto, o compilador não pode inserir informações de tipo de interoperabilidade desse assembly, porque outro assembly que você referenciou (assembly2) também faz referência a esse assembly (assembly1) e tem a propriedade `Embed Interop Types` definida como `False`.</span><span class="sxs-lookup"><span data-stu-id="874ae-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="874ae-108">Configurar a propriedade `Embed Interop Types` em uma referência de assembly como `True` é equivalente à referenciar o assembly usando a opção `/link` para o compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="874ae-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="874ae-109">**ID do erro:** BC40059</span><span class="sxs-lookup"><span data-stu-id="874ae-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="874ae-110">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="874ae-110">To address this warning</span></span>  
  
- <span data-ttu-id="874ae-111">Para inserir informações de tipo de interoperabilidade para os dois assemblies, defina a propriedade `Embed Interop Types` em todas as referências ao assembly1 como `True`.</span><span class="sxs-lookup"><span data-stu-id="874ae-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
- <span data-ttu-id="874ae-112">Para remover o aviso, você pode definir a propriedade `Embed Interop Types` do assembly1 como `False`.</span><span class="sxs-lookup"><span data-stu-id="874ae-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="874ae-113">Nesse caso, as informações de tipo de interoperabilidade são fornecidas por um assembly de interoperabilidade primário (PIA).</span><span class="sxs-lookup"><span data-stu-id="874ae-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874ae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="874ae-114">See also</span></span>

- [<span data-ttu-id="874ae-115">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="874ae-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="874ae-116">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="874ae-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
