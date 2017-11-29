---
title: ICorDebugExceptionObjectCallStackEnum (Interfaz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords: ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4814de2de71ba0fa4d1400f0be27fa4942febf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="83b7e-102">ICorDebugExceptionObjectCallStackEnum (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="83b7e-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="83b7e-103">Proporciona un enumerador para la información de la pila de llamadas que está incrustada en un objeto de excepción.</span><span class="sxs-lookup"><span data-stu-id="83b7e-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="83b7e-104">Esta interfaz es una subclase de ICorDebugEnum (interfaz).</span><span class="sxs-lookup"><span data-stu-id="83b7e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83b7e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="83b7e-105">Methods</span></span>  
  
|<span data-ttu-id="83b7e-106">Método</span><span class="sxs-lookup"><span data-stu-id="83b7e-106">Method</span></span>|<span data-ttu-id="83b7e-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="83b7e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83b7e-108">Icordebugexceptionobjectcallstackenum:: Next</span><span class="sxs-lookup"><span data-stu-id="83b7e-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="83b7e-109">Obtiene un número especificado de [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos que contienen información acerca de la pila de llamadas de un objeto de excepción.</span><span class="sxs-lookup"><span data-stu-id="83b7e-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83b7e-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="83b7e-110">Remarks</span></span>  
 <span data-ttu-id="83b7e-111">El `ICorDebugExceptionObjectCallStackEnum` interfaz implementa ICorDebugEnum (interfaz).</span><span class="sxs-lookup"><span data-stu-id="83b7e-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="83b7e-112">Un `ICorDebugExceptionObjectCallStackEnum` instancia se rellena con [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objetos mediante una llamada a la [icordebugexceptionobjectvalue:: Enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="83b7e-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="83b7e-113">Se pueden enumerar los elementos de la pila de llamadas en la colección mediante una llamada a la [icordebugexceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) (método)</span><span class="sxs-lookup"><span data-stu-id="83b7e-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b7e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83b7e-114">Requirements</span></span>  
 <span data-ttu-id="83b7e-115">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83b7e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83b7e-116">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83b7e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83b7e-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83b7e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83b7e-118">**Versiones de .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83b7e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b7e-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="83b7e-119">See Also</span></span>  
 [<span data-ttu-id="83b7e-120">Interfaces de depuración</span><span class="sxs-lookup"><span data-stu-id="83b7e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="83b7e-121">Depuración</span><span class="sxs-lookup"><span data-stu-id="83b7e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)