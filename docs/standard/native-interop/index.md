---
title: Interoperabilidade Nativa – .NET
description: Saiba como fazer interface com componentes nativos no .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 29aacc9210b4103f379b7776c36fc3c29b9e6dec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973546"
---
# <a name="native-interoperability"></a><span data-ttu-id="849b8-103">Interoperabilidade nativa</span><span class="sxs-lookup"><span data-stu-id="849b8-103">Native interoperability</span></span>

<span data-ttu-id="849b8-104">Os artigos a seguir mostram várias maneiras de fazer "interoperabilidade nativa" no .NET.</span><span class="sxs-lookup"><span data-stu-id="849b8-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="849b8-105">Existem alguns motivos para chamar em código nativo:</span><span class="sxs-lookup"><span data-stu-id="849b8-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="849b8-106">Os sistemas operacionais vêm com um grande volume de APIs que não estão presentes nas bibliotecas de classes gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="849b8-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="849b8-107">Um exemplo perfeito para esse cenário seria o acesso a funções de gerenciamento de hardware ou do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="849b8-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="849b8-108">Comunicação com outros componentes que têm ou podem produzir ABIs de estilo C (ABIs nativas), como o código Java que é exposto via [JNI (Interface Nativa do Java)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou qualquer outra linguagem gerenciada que pode produzir um componente nativo.</span><span class="sxs-lookup"><span data-stu-id="849b8-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="849b8-109">No Windows, a maioria dos softwares que são instalados, como o pacote Microsoft Office, registra os componentes COM que representam seus programas e permitem que sejam automatizados ou usados pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="849b8-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="849b8-110">Isso também requer interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="849b8-110">This also requires native interoperability.</span></span>

<span data-ttu-id="849b8-111">A lista acima não abrange todas as possíveis situações e cenários em que o desenvolvedor desejaria/gostaria de/precisaria fazer interface com componentes nativos.</span><span class="sxs-lookup"><span data-stu-id="849b8-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="849b8-112">A biblioteca de classes do .NET, por exemplo, usa o suporte para interoperabilidade nativa para implementar um número razoável de APIs, como suporte ao console e manipulação, acesso ao sistema de arquivos e outras.</span><span class="sxs-lookup"><span data-stu-id="849b8-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="849b8-113">No entanto, é importante observar que há uma opção, se necessário.</span><span class="sxs-lookup"><span data-stu-id="849b8-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="849b8-114">A maioria dos exemplos nesta seção será apresentada para todas as três plataformas com suporte para .NET Core (Windows, Linux e macOS).</span><span class="sxs-lookup"><span data-stu-id="849b8-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="849b8-115">No entanto, para alguns exemplos ilustrativos e curtos, é exibida apenas uma amostra que usa nomes de arquivo e extensões do Windows (ou seja, "dll" para bibliotecas).</span><span class="sxs-lookup"><span data-stu-id="849b8-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="849b8-116">Isso não significa que tais recursos não estão disponíveis em Linux ou macOS; foi feito simplesmente para maior conveniência.</span><span class="sxs-lookup"><span data-stu-id="849b8-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="849b8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="849b8-117">See also</span></span>

- [<span data-ttu-id="849b8-118">Invocação de plataforma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="849b8-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="849b8-119">Marshalling dos tipos</span><span class="sxs-lookup"><span data-stu-id="849b8-119">Type marshalling</span></span>](type-marshalling.md)
- [<span data-ttu-id="849b8-120">Melhores práticas de interoperabilidade nativa</span><span class="sxs-lookup"><span data-stu-id="849b8-120">Native interoperability best practices</span></span>](best-practices.md)
