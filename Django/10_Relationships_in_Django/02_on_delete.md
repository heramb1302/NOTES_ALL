**1. Create a super user**
**2. Add some data to husband and wife table through super user**

*husband = models.OneToOneField(Husband, on_delete=models.CASCADE)*:
This allows to delete the wife ass we delete the husband 


*husband = models.OneToOneField(Husband, on_delete=models.PROTECT)*
if we try to delete the husband which having wife it will not delete the husband , but if has no wife it will deleted the husband!
![[Pasted image 20260513143939.png]]
![[Pasted image 20260513143947.png]]



![[Pasted image 20260513144001.png]]
![[Pasted image 20260513144013.png]]






*husband = models.OneToOneField(Husband, on_delete=models.SET_NULL)*
This will allow to delete the husband but wife remain in database and husband value for wife will set to Null.
