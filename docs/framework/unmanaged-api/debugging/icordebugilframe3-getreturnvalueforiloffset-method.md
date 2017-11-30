---
title: "ICorDebugILFrame3::GetReturnValueForILOffset (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6e51043fe3824154f1333969134209a685f98914
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="560df-102">ICorDebugILFrame3::GetReturnValueForILOffset (Método)</span><span class="sxs-lookup"><span data-stu-id="560df-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="560df-103">Obtiene un objeto de "ICorDebugValue" que encapsula el valor devuelto de una función.</span><span class="sxs-lookup"><span data-stu-id="560df-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="560df-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="560df-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="560df-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="560df-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="560df-106">Desplazamiento IL.</span><span class="sxs-lookup"><span data-stu-id="560df-106">The IL offset.</span></span> <span data-ttu-id="560df-107">Vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="560df-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="560df-108">Un puntero a la dirección de un objeto de interfaz de "ICorDebugValue" que proporciona información sobre el valor devuelto de una llamada de función.</span><span class="sxs-lookup"><span data-stu-id="560df-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="560df-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="560df-109">Remarks</span></span>  
 <span data-ttu-id="560df-110">Este método se utiliza junto con la [icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método para obtener el valor devuelto de un método.</span><span class="sxs-lookup"><span data-stu-id="560df-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="560df-111">Resulta especialmente útil en el caso de los métodos cuyos valores devueltos se omiten, como en los dos ejemplos de código siguientes.</span><span class="sxs-lookup"><span data-stu-id="560df-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="560df-112">El primer ejemplo llama al método <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, pero omite el valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="560df-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="560df-113">El segundo ejemplo muestra un problema mucho más común de depuración.</span><span class="sxs-lookup"><span data-stu-id="560df-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="560df-114">Dado que se usa un método como argumento en una llamada al método, solo se puede tener acceso al valor devuelto cuando el depurador recorre el método llamado.</span><span class="sxs-lookup"><span data-stu-id="560df-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="560df-115">En muchos casos, especialmente cuando el método al que se llama se define en una biblioteca externa, eso no es posible.</span><span class="sxs-lookup"><span data-stu-id="560df-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="560df-116">Si se pasa el [icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método desplazamiento IL a un sitio de llamada de función, devuelve uno o varios desplazamientos nativos.</span><span class="sxs-lookup"><span data-stu-id="560df-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="560df-117">El depurador puede establecer puntos de interrupción en estos desplazamientos nativos en la función.</span><span class="sxs-lookup"><span data-stu-id="560df-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="560df-118">Cuando el depurador llega a uno de los puntos de interrupción, podrá pasar el mismo desplazamiento IL que pasó a este método para obtener el valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="560df-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="560df-119">A continuación, el depurador debe borrar todos los puntos de interrupción que estableció.</span><span class="sxs-lookup"><span data-stu-id="560df-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="560df-120">El [icordebugcode3:: Getreturnvalueliveoffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) y `ICorDebugILFrame3::GetReturnValueForILOffset` métodos permiten obtener información del valor devuelto para solo los tipos de referencia.</span><span class="sxs-lookup"><span data-stu-id="560df-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="560df-121">La recuperación de información de valor devuelto de tipos de valor (es decir, todos los tipos derivados de <xref:System.ValueType>) no se admite.</span><span class="sxs-lookup"><span data-stu-id="560df-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="560df-122">El desplazamiento IL especificado por el `ILOffset` parámetro debe estar en un sitio de llamada de función y el código depurado debe detenerse en un punto de interrupción en el desplazamiento nativo devuelto por la [icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) (método) para el mismo desplazamiento IL.</span><span class="sxs-lookup"><span data-stu-id="560df-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="560df-123">Si el código que se está depurando no se detiene en la ubicación correcta para el desplazamiento IL especificado, se producirá un error en la API.</span><span class="sxs-lookup"><span data-stu-id="560df-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="560df-124">Si la llamada de función no devuelve un valor, se producirá un error en la API.</span><span class="sxs-lookup"><span data-stu-id="560df-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="560df-125">El método `ICorDebugILFrame3::GetReturnValueForILOffset` solo está disponible en los sistemas basados en x86 y AMD64.</span><span class="sxs-lookup"><span data-stu-id="560df-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="560df-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="560df-126">Requirements</span></span>  
 <span data-ttu-id="560df-127">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="560df-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="560df-128">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="560df-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="560df-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="560df-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="560df-130">**Versiones de .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="560df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560df-131">Vea también</span><span class="sxs-lookup"><span data-stu-id="560df-131">See Also</span></span>  
 [<span data-ttu-id="560df-132">GetReturnValueLiveOffset (método)</span><span class="sxs-lookup"><span data-stu-id="560df-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="560df-133">ICorDebugILFrame3 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="560df-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)