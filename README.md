# Documentation-API
drf-yasg


# Etape 1 :  Installation 

      pip install drf-yasg

# Etape 2 : Dans settings.py 

      INSTALLED_APPS = [
         ...
         'drf_yasg',
         ...
      ]

# Etape 3 : Dans urls.py du projet

      from drf_yasg.views import get_schema_view
      from drf_yasg import openapi

      schema_view = get_schema_view(
         openapi.Info(
            title="Snippets API",
            default_version='v1',
            description="Test description",
            terms_of_service="https://www.google.com/policies/terms/",
            contact=openapi.Contact(email="contact@snippets.local"),
            license=openapi.License(name="BSD License"),
         ),
         validators=['flex', 'ssv'],
         public=True,
         permission_classes=(permissions.AllowAny,),
      )
      urlpatterns = [
         url(r'^swagger(?P<format>\.json|\.yaml)$', schema_view.without_ui(cache_timeout=None), name='schema-json'),
         url(r'^swagger/$', schema_view.with_ui('swagger', cache_timeout=None), name='schema-swagger-ui'),
         url(r'^redoc/$', schema_view.with_ui('redoc', cache_timeout=None), name='schema-redoc'),
         ...
      ]

