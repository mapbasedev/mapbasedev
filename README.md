# Mapbase

[Mapbase](https://mapbase.dev) is an open source map stack built on top of [supabase](https://supabase.com).

## How it works

Mapbase is a combination of open source tools.
We're building the features of a modern map stack using open source products.

We are using
- [Maplibre](https://maplibre.org) the open source map rendering library for rendering vector tiles
- [Protomaps](https://protomaps.com) the open source vector tile file format for distributing map data
- [OpenStreetMap](https://www.openstreetmap.org) the open and free geographic map dataset

and mapping it to
- [supabase storage](https://supabase.com/docs/guides/storage) to store and distribute the map data as Protomaps .pmtiles files
- [supabase database](https://supabase.com/docs/guides/database) for persisting geospatial data such as points and lines
- [supabase realtime](https://supabase.com/docs/guides/realtime) for geospatial data such as routes updating in real-time
- [supabase auth](https://supabase.com/docs/guides/auth) for authentication and authorization for the geospatial map data


## Notes

1. Set up multi-factor authentication https://supabase.com/dashboard/account/security
2. Create a personal access token https://supabase.com/dashboard/account/tokens

Supabase API docs: https://api.supabase.com/api/v1

```bash
export SUPABASE_ACCESS_TOKEN="spb_xxxxxxxxxx"

curl -sSf --proto =https --tlsv1.3 -H "Authorization: Bearer $SUPABASE_ACCESS_TOKEN" https://api.supabase.com/v1/organizations

curl -sSf --proto =https --tlsv1.3 -H "Authorization: Bearer $SUPABASE_ACCESS_TOKEN" https://api.supabase.com/v1/projects
```


### Auth

Auth issues JWTs to users: these JWTs encode an authenticated user in the system or an anonymous user.
Other services like supabase database can then check if a user is allowed to access database records based on the JWT.

Helpers for React
- https://www.npmjs.com/package/@supabase/auth-helpers-react
- https://github.com/supabase/auth-helpers/blob/main/packages/react/src/components/SessionContext.tsx


### Storage

Are byte-range requests not supported? https://github.com/supabase/storage/issues/322

The protomaps protocol makes byte-range requests against a hosted .pmtiles file. Will this be a hard blocker for hosting maps on supabase storage?


### Database

tbd


### Realtime

tbd
