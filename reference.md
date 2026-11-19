# Reference
## Profiles
<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L33-L57">list</a>() -> ListProfilesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The brands or clients the team posts for, each with its colour and time zone. A key or person limited to some profiles gets those only.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L59-L111">create</a>(...) -> Profile</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A brand or client of its own, with no accounts yet: connect them with `Get a link to connect an account`, or in the web app. Each profile's name is its own in the team (409 otherwise).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.create(
    name="Bloom Studio",
    time_zone="Europe/Lisbon",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**name:** `str` — The brand or client's name, up to 60 characters.
    
</dd>
</dl>

<dl>
<dd>

**color:** `typing.Optional[str]` — Hex colour for the profile's tile, such as #4FA3FF; one is picked when left out.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — An IANA time zone, such as Europe/Lisbon.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L113-L142">delete</a>(...) -> DeleteProfilesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

For good: what is in it cannot be restored. Its posts go, deleted ones included, with their history and preview links (posts already published stay on the networks), and so do its posting times, its upload requests and connect links, its other events, and its media that no post of another profile uses. Its short links stay and keep working, with no profile. People and invitations limited to some profiles, API keys, agents and webhook endpoints lose it from their profiles: a key or agent that reached only this profile is revoked, and an endpoint that took only its events is disabled (`disabledReason` `profile_deleted`). Refused (409) while it has accounts (move each to another profile, or remove it, first), when it is the team's only profile, while one of its posts is going out, and while a person or an open invitation reaches no other profile, naming them. Only an owner deletes a profile, signed in as themselves within the last 15 minutes (with their session, as the web app does), or an API key an owner let remove accounts and delete profiles when making it (Developers in the web app). Other API keys and agents are refused (403), and a key reaches only its own profiles.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.delete(
    id="prof_01m41bamm0f3a8mr2eek4wdq39",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The profile's id (`prof_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L144-L193">update</a>(...) -> Profile</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Its name, colour or time zone; what is left out stays as it is. A new time zone reads posting times and local `scheduledAt` from then on: posts already scheduled keep their time.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.update(
    id="prof_01m40k9k80fxd8cvng8derm7g9",
    color="#3CCF96",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The profile's id (`prof_`).
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — A new name, up to 60 characters, not another profile's.
    
</dd>
</dl>

<dl>
<dd>

**color:** `typing.Optional[str]` — Hex colour for the profile's tile, such as #4FA3FF.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — An IANA time zone, such as Europe/Lisbon.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L195-L229">queue</a>(...) -> Queue</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Its posting times, read in its time zone; the next `count` times free for at least one of its accounts, with which ones (none of them has a post at that minute, scheduled or queued, and none would pass its network's daily cap); and its queued posts still to go out.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.queue(
    id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The profile's id (`prof_`).
    
</dd>
</dl>

<dl>
<dd>

**count:** `typing.Optional[int]` — How many free times to list.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.profiles.<a href="src/rizamo/profiles/client.py#L231-L279">set_queue</a>(...) -> Queue</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Replaces the profile's posting times with these, the whole week in one call; an empty list empties it. At most 24 a day, each once. Each is a local time in the profile's time zone, the same clock time all year. Posts already queued keep their times; only new ones take the new week.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo, QueueSlot
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.profiles.set_queue(
    id="prof_01m40k9k80fxd8cvng8derm7g9",
    slots=[
        QueueSlot(
            weekday="mon",
            time="09:00",
        ),
        QueueSlot(
            weekday="wed",
            time="12:30",
        ),
        QueueSlot(
            weekday="fri",
            time="18:00",
        )
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The profile's id (`prof_`).
    
</dd>
</dl>

<dl>
<dd>

**slots:** `typing.List[QueueSlot]` — The whole week, each time a weekday and a local time, at most 24 a day. An empty list empties the queue.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Accounts
<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L39-L91">list</a>(...) -> ListAccountsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every account without `limit`; with it, a page at a time: pass `nextCursor` as `cursor` for the next one, with the same filters.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.list(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[ListAccountsRequestStatus]` — connected: works. expiring: reconnect before `reconnectBy`. disconnected: the network revoked access; reconnect to publish again.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return. Left out: every account.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before, with the same filters.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L93-L122">get</a>(...) -> Account</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One connected account: its network, handle, profile, status, billing, what it can do (`capabilities`) and the formats it publishes.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.get(
    id="acc_01m423bp00fz39kp5pc7m42tsw",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The account's id (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L124-L153">remove</a>(...) -> AccountRemoved</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

It stops publishing and is no longer billed, and nothing changes on its network. Its posts: one that goes to it alone moves to Deleted (`post.deleted`), scheduled, draft or published, and can be restored for 30 days; one with other accounts keeps them, loses this account's part that never went out (`post.updated`) and keeps the part that did, with its `url` and without its numbers (`accountRemoved` on the target). The answer counts them by status (`Preview removing an account` counts them before). Its name, picture and followers go at once; its handle stays to name those parts, with their links, for as long as their posts exist. What Rizamo read from the network about its posts there is deleted, and so are its comments and messages in the inbox, with the events that carry them (`comment.received`, `message.received`, `message.sent`, `comment_automation.*`) and their webhook deliveries. Its comment automations are paused (each with a `comment_automation.paused` event) and their runs deleted with the comments, so their numbers start again from zero and people they answered may be answered once more. It is told as `account.removed` with `reason` `removed_by_team`, never `account.disconnected`, which is a lost login. Connecting it again brings back the same account, its automations paused, to resume; posts in Deleted are restored by hand. Removing an account changes the bill, so only owners remove one, or an API key an owner let remove accounts and delete profiles when making it (Developers in the web app); other API keys are refused (403).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.remove(
    id="acc_01m44bet40enpr62nh6w01e67r",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The account's id (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L155-L188">update</a>(...) -> Account</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Moves the account to another profile you reach: from then on it is that profile's, for the people, keys and agents who reach it, and its old profile's stop seeing it. Events already written stay in the profile they happened in.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.update(
    id="acc_01m423bp00fz39kp5pc7m42tsw",
    profile_id="prof_01m41bamm0f3a8mr2eek4wdq39",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The account's id (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `str` — The profile (`prof_`) it moves to.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L190-L221">tiktok_creator_info</a>(...) -> TikTokCreatorInfo</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

What TikTok's posting screen needs, read from TikTok now: the creator's name and picture, who can see a photo post, whether the account turned comments, Duet or Stitch off, and the longest video it may post. TikTok asks apps to show the creator's name and these choices before every post.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.tiktok_creator_info(
    id="acc_01m43kdrr0ebxa6wpz9f3zmaqa",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The TikTok account's id (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L223-L280">search_music</a>(...) -> SearchMusicAccountsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Tracks the account may put on a post, from its network's library. TikTok: its Commercial Music Library's trending list (up to 100), filtered by genre, country and period; there is no search. The same filters answer the same list for 30 minutes, and searches beyond Rizamo's limits on TikTok answer 429 with when to try again. Instagram (accounts connected through Facebook Login): a search with `q`, or what is trending without it, up to 25, music or original sounds. Facebook adds no music through its API. A filter of the other network is refused. Attach a track's `id` in the target's `music` option.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.search_music(
    id="acc_01m43kdrr0ebxa6wpz9f3zmaqa",
    country="PT",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The account (`acc_`) the post goes to: a TikTok account, or an Instagram account connected through Facebook Login.
    
</dd>
</dl>

<dl>
<dd>

**q:** `typing.Optional[str]` — Instagram: words to search for. Left out, Instagram's trending tracks. TikTok has no search.
    
</dd>
</dl>

<dl>
<dd>

**type:** `typing.Optional[SearchMusicAccountsRequestType]` — Instagram: music (the default) or original sounds from other reels.
    
</dd>
</dl>

<dl>
<dd>

**genre:** `typing.Optional[SearchMusicAccountsRequestGenre]` — TikTok: one of TikTok's genres. Default ALL.
    
</dd>
</dl>

<dl>
<dd>

**country:** `typing.Optional[str]` — TikTok: where the tracks are trending, as a two-letter code such as PT. Default US (TikTok's).
    
</dd>
</dl>

<dl>
<dd>

**period:** `typing.Optional[SearchMusicAccountsRequestPeriod]` — TikTok: trending over the last day, week (the default), 30 or 90 days.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.accounts.<a href="src/rizamo/accounts/client.py#L282-L311">removal</a>(...) -> AccountRemoval</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

What removing the account would do to the posts that use it, counted now, with nothing changed: show it to the person before they confirm. `Remove an account` answers the same counts once it is done.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.accounts.removal(
    id="acc_01m44bet40enpr62nh6w01e67r",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The account's id (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Connect
<details><summary><code>client.connect.<a href="src/rizamo/connect/client.py#L27-L89">link</a>(...) -> ConnectLink</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A link to send a person to within 30 minutes: it goes straight to the network, and connects accounts once (a preview or a second browser that opens it uses nothing up). They log in on the network, with no Rizamo account, and come back to `redirectUrl`, or, without one, land on a Rizamo page that says what was connected (for a chat agent, a script or n8n). `instagram` is Instagram Login, for an Instagram professional account on its own; `facebook` is Facebook Login, its Pages and the Instagram accounts linked to them, which can also add music to reels and get each story's final numbers when it ends (deleting Instagram posts will need it too, once Meta reviews Rizamo's access). LinkedIn connects in the web app only, as LinkedIn's terms ask: no connect link offers it. Once connected there, LinkedIn accounts publish and report through the API and MCP.

A login that reaches one new account the key may add connects it at once; one that reaches several (Pages, YouTube channels), or an account already in the team, shows the person a page to pick them, with only new accounts ticked. An account already in the team in a profile the key does not reach is never added. With `connectionId`, only that login's accounts are renewed.

Back at `redirectUrl`, Rizamo adds `status` (connected or error), `network`, `profileId`, and either `accountIds` with each one's `billing` in the same order, comma-separated, or `error` (cancelled, refused, no_accounts, expired, used, unavailable, forbidden, gone, failed) and `message`. Nothing in it works without your key: read the accounts with `GET /accounts/{id}`. A return can arrive more than once (a reload): take `GET /accounts` (`list_accounts`) as the truth. A link opened once it is used or expired, or after your key lost access, stays on a Rizamo page that says why: only a person back from the network comes to `redirectUrl`.

Accounts are billed as in the web app: the first 2 free. On the free plan the rest arrive `awaiting_payment` until an owner starts a plan. On a paid plan they are charged at once to the card on file: your call is the consent. A charge that needs the card holder, or more accounts than the owner lets the API add this period, leaves them `awaiting_payment` until an owner pays in the web app. The person connecting never sees prices.

With `connectionId`, the person logs in again for that login's accounts (an expired login): only accounts already in the team are updated, and `network` must be the login's.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.connect.link(
    network="facebook",
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
    redirect_url="https://example.com/rizamo/connected",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**network:** `LinkConnectRequestNetwork` — Where the person logs in: instagram (Instagram Login, a professional account on its own), facebook (Facebook Login: Pages and the Instagram accounts linked to them), tiktok, threads or youtube. LinkedIn connects in the web app only, as LinkedIn's terms ask: no connect link offers it. Once connected there, LinkedIn accounts publish and report through the API and MCP.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — The profile (`prof_`) new accounts go to. Required unless `connectionId` is given.
    
</dd>
</dl>

<dl>
<dd>

**redirect_url:** `typing.Optional[str]` — Where the person comes back to: an absolute https address, or http://localhost or http://127.0.0.1 (any port) while you develop. Fixed in the link: nothing the person does can change it. Leave it out when you have no address (a chat agent, a script): the person lands on a Rizamo page that names what was connected, or says why not.
    
</dd>
</dl>

<dl>
<dd>

**connection_id:** `typing.Optional[str]` — Log in again for this login (`Account.connectionId`), to renew it.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Fields
<details><summary><code>client.fields.<a href="src/rizamo/fields/client.py#L34-L66">list</a>(...) -> ListFieldsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The team's custom fields, with their keys, types and choices: set them on posts with `fields`, and filter posts and analytics by them.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.fields.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entity:** `typing.Optional[ListFieldsRequestEntity]` — Only fields on this kind of object: post, the only kind today.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.fields.<a href="src/rizamo/fields/client.py#L68-L138">create</a>(...) -> FieldDefinition</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A field every post can carry, such as a campaign. Its key and type cannot change, and a key is used once per team (409 otherwise).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.fields.create(
    key="campaign",
    label="Campaign",
    type="select",
    options=[
        "Winter menu",
        "Brunch"
    ],
    description="The campaign a post belongs to.",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**key:** `str` — Lowercase letters, digits and underscores, starting with a letter. It cannot change.
    
</dd>
</dl>

<dl>
<dd>

**label:** `str` — Its name for people, up to 60 characters: "Campaign".
    
</dd>
</dl>

<dl>
<dd>

**type:** `CreateFieldsRequestType` — text, select, multi_select, number, url, date or checkbox. It cannot change.
    
</dd>
</dl>

<dl>
<dd>

**entity:** `typing.Optional[CreateFieldsRequestEntity]` — What the field is on: post, the only kind today.
    
</dd>
</dl>

<dl>
<dd>

**options:** `typing.Optional[typing.List[str]]` — The choices of a select or multi_select field. Required for those, refused for the others.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — What the field is for, up to 200 characters, shown to people and agents.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.fields.<a href="src/rizamo/fields/client.py#L140-L169">delete</a>(...) -> DeleteFieldsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The field goes from the team, and its values are removed from every post.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.fields.delete(
    key="campaign",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**key:** `str` — The field's key, such as campaign.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.fields.<a href="src/rizamo/fields/client.py#L171-L220">update</a>(...) -> FieldDefinition</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The key and type cannot change. Removing an option leaves the value on posts that have it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.fields.update(
    key="campaign",
    options=[
        "Winter menu",
        "Brunch",
        "Pastry week"
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**key:** `str` — The field's key, such as campaign.
    
</dd>
</dl>

<dl>
<dd>

**label:** `typing.Optional[str]` — A new name for people, up to 60 characters.
    
</dd>
</dl>

<dl>
<dd>

**options:** `typing.Optional[typing.List[str]]` — A select or multi_select field's choices as they should be, every one of them. A choice left out stays on the posts that have it.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — What the field is for; null removes it.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Posts
<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L50-L141">list</a>(...) -> ListPostsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The team's posts, ordered by when they go out: their `scheduledAt`, or when they were created if they have none. The latest first, or the earliest first with `order` asc. A page at a time: pass `nextCursor` as `cursor` for the next one, with the same filters and `order`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.list(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**status:** `typing.Optional[PostStatus]` — Only posts with this status.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `typing.Optional[str]` — Posts with a target on this account (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**from:** `typing.Optional[datetime.datetime]` — Posts whose time is this or later. A post's time is its `scheduledAt` (when it goes or went out; publishing now sets it), or its `createdAt` when it has none, such as a draft with no date. Inclusive.
    
</dd>
</dl>

<dl>
<dd>

**to:** `typing.Optional[datetime.datetime]` — Posts whose time, as for `from`, is this or earlier. Inclusive.
    
</dd>
</dl>

<dl>
<dd>

**q:** `typing.Optional[str]` — Posts whose text has this, in any case.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, str]]` — Only posts whose custom fields have these values, for example `fields[campaign]=Winter menu`. A multi_select field matches when it has the value.
    
</dd>
</dl>

<dl>
<dd>

**deleted:** `typing.Optional[ListPostsRequestDeleted]` — Deleted posts are left out unless asked: `only` lists the ones that can still be restored.
    
</dd>
</dl>

<dl>
<dd>

**order:** `typing.Optional[ListPostsRequestOrder]` — `desc`, the latest first, or `asc`, the earliest first: with `from` and `to`, `asc` reads a period forward.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before, with the same filters and `order`.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 200: 100 when left out.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L143-L253">create</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A draft (the default), a post scheduled at `scheduledAt`, or one queued at its profile's next free posting time (`queue: true`), to one or more accounts of one profile. Each target is an account and a format, with its own text, files, options and first comment when it needs them. What a network would refuse is refused now with the reason, such as a first comment where the network takes none, or a story's own text on Instagram or Facebook; what only stops a post from going out, such as TikTok's choices on a draft, waits until it is scheduled. `Check a post without creating it` lists every problem at once. To publish now, create it, then `Publish a post now`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
from rizamo.posts import CreatePostsRequestTargetsItem
import datetime

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.create(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
    text="Winter menu is here: spiced orange latte and our first pastel de nata of the season. Open from 8 tomorrow.",
    targets=[
        CreatePostsRequestTargetsItem(
            account_id="acc_01m423bp00fz39kp5pc7m42tsw",
            format="feed",
            first_comment="Full menu: go.rizamo.com/k7Qm2p",
        ),
        CreatePostsRequestTargetsItem(
            account_id="acc_01m42vcqc0e15apwrdjth3v2q5",
        ),
        CreatePostsRequestTargetsItem(
            account_id="acc_01m44bet40enpr62nh6w01e67r",
            text="Winter menu is here: spiced orange latte and our first pastel de nata of the season.",
        )
    ],
    media_ids=[
        "med_01m48vn2c0emgvm8bkwtj1hayp"
    ],
    scheduled_at=datetime.datetime.fromisoformat("2026-11-06T09:00:00+00:00"),
    fields={
        "campaign": "Winter menu"
    },
    status="scheduled",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `str` — The profile (`prof_`) the post is for: the brand whose accounts it goes to.
    
</dd>
</dl>

<dl>
<dd>

**text:** `str` — The caption, on every target that has no text of its own. A draft may have none; to go out, each target needs a text or a file (or for Facebook a `link`).
    
</dd>
</dl>

<dl>
<dd>

**targets:** `typing.List[CreatePostsRequestTargetsItem]` — Where the post goes, up to 100. Each target is one account and format: one Instagram account can take a reel and a story of the same post.
    
</dd>
</dl>

<dl>
<dd>

**media_ids:** `typing.Optional[typing.List[str]]` — Its files (`med_`, from Add media or an upload request), in order: on every target that has none of its own.
    
</dd>
</dl>

<dl>
<dd>

**chain:** `typing.Optional[typing.List[CreatePostsRequestChainItem]]` — More posts after the first, each published as a reply to the one before: a thread on Threads (up to 24 more). Networks that publish chains get every part; the others get the first post alone.
    
</dd>
</dl>

<dl>
<dd>

**scheduled_at:** `typing.Optional[datetime.datetime]` — When it goes out, with `status` scheduled: exact with `Z` or an offset, else a local time in `timeZone` or the profile's. Never with `queue: true`.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — Reads a `scheduledAt` without an offset; the profile's time zone when left out.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, typing.Optional[CreatePostsRequestFieldsValue]]]` — Custom field values by key (List custom fields), such as `{ "campaign": "Winter menu" }`.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[CreatePostsRequestStatus]` — draft (the default) never publishes. scheduled needs a future `scheduledAt`, or `queue: true`.
    
</dd>
</dl>

<dl>
<dd>

**queue:** `typing.Optional[bool]` — Schedules it at the next time of its profile's queue (`Get a profile's queue`) when none of its accounts has a post then and none would pass its network's daily cap, up to 90 days ahead. Instead of `scheduledAt`, never with it; `status` becomes scheduled, and the answer's `scheduledAt` is the time it took. A queue with no times answers `queue_empty`, one with none free `queue_full`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L255-L284">get</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One post with each target's status, link and error, and what Rizamo does to its files (`changes`). `List events` with its id has its history: why a target failed is in its `post.target.failed` event too.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.get(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L286-L315">delete</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The post is kept, marked deleted, and can be restored for 30 days, then goes for good unless a target is still live on its network. Live targets are removed from their networks where they allow it: each target's `removal` says what happened. Deleting it again retries the ones that failed.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.delete(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L317-L410">update</a>(...) -> UpdatePostsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Changes its text, files, chain, time, targets or fields, schedules a draft (`status` scheduled with a future `scheduledAt`, or `queue: true`), or moves a scheduled post back to draft; what is left out stays as it is. Targets already live change on their network only with `applyToPublished`, where the network allows it, and `edits` says what happened to each.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
import datetime

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.update(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
    scheduled_at=datetime.datetime.fromisoformat("2026-11-06T10:30:00+00:00"),
    time_zone="Europe/Lisbon",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**text:** `typing.Optional[str]` — The new caption, on every target that has no text of its own.
    
</dd>
</dl>

<dl>
<dd>

**media_ids:** `typing.Optional[typing.List[str]]` — Its files (`med_`, from Add media or an upload request), in order: on every target that has none of its own.
    
</dd>
</dl>

<dl>
<dd>

**chain:** `typing.Optional[typing.List[UpdatePostsRequestChainItem]]` — The chain as it should be: targets not live yet take it. A live target's chain does not change.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[UpdatePostsRequestStatus]` — scheduled schedules a draft (with a future `scheduledAt`, or `queue: true`); draft moves a scheduled post back.
    
</dd>
</dl>

<dl>
<dd>

**scheduled_at:** `typing.Optional[datetime.datetime]` — A new time: exact with `Z` or an offset, else a local time in `timeZone` or the profile's. Null takes a draft's time away. Never with `queue: true`.
    
</dd>
</dl>

<dl>
<dd>

**queue:** `typing.Optional[bool]` — Schedules it at the next time of its profile's queue (`Get a profile's queue`) when none of its accounts has a post then and none would pass its network's daily cap, up to 90 days ahead. Instead of `scheduledAt`, never with it; `status` becomes scheduled, and the answer's `scheduledAt` is the time it took. A queue with no times answers `queue_empty`, one with none free `queue_full`.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — Reads a `scheduledAt` without an offset; the profile's time zone when left out.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, typing.Optional[UpdatePostsRequestFieldsValue]]]` — Custom field values by key (List custom fields), such as `{ "campaign": "Winter menu" }`.
    
</dd>
</dl>

<dl>
<dd>

**targets:** `typing.Optional[typing.List[UpdatePostsRequestTargetsItem]]` — The targets as they should be. Pending ones not listed are dropped and new ones added; live ones stay and change only with `applyToPublished`.
    
</dd>
</dl>

<dl>
<dd>

**apply_to_published:** `typing.Optional[bool]` — Also edit targets already live, where the network allows it. Each one's result is in `edits`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L412-L515">validate</a>(...) -> ValidatePostsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Takes what Create a post takes and creates nothing. `problems` are what would stop it now; `warnings` are what would stop it from being scheduled or published later, such as Instagram without an image or a video. Each target says what Rizamo would do to its files, and `scheduledAt` when it would go out (with `queue: true`, the queue's next time free for all of its accounts).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
from rizamo.posts import ValidatePostsRequestTargetsItem

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.validate(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
    text="Winter menu is here: spiced orange latte and our first pastel de nata of the season. Open from 8 tomorrow.",
    targets=[
        ValidatePostsRequestTargetsItem(
            account_id="acc_01m423bp00fz39kp5pc7m42tsw",
            format="reel",
        ),
        ValidatePostsRequestTargetsItem(
            account_id="acc_01m423bp00fz39kp5pc7m42tsw",
            format="story",
        ),
        ValidatePostsRequestTargetsItem(
            account_id="acc_01m43kdrr0ebxa6wpz9f3zmaqa",
        )
    ],
    media_ids=[
        "med_01m49kp3r0ed9szw9jcadbjdp1"
    ],
    status="draft",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `str` — The profile (`prof_`) the post is for: the brand whose accounts it goes to.
    
</dd>
</dl>

<dl>
<dd>

**text:** `str` — The caption, on every target that has no text of its own. A draft may have none; to go out, each target needs a text or a file (or for Facebook a `link`).
    
</dd>
</dl>

<dl>
<dd>

**targets:** `typing.List[ValidatePostsRequestTargetsItem]` — Where the post goes, up to 100. Each target is one account and format: one Instagram account can take a reel and a story of the same post.
    
</dd>
</dl>

<dl>
<dd>

**media_ids:** `typing.Optional[typing.List[str]]` — Its files (`med_`, from Add media or an upload request), in order: on every target that has none of its own.
    
</dd>
</dl>

<dl>
<dd>

**chain:** `typing.Optional[typing.List[ValidatePostsRequestChainItem]]` — More posts after the first, each published as a reply to the one before: a thread on Threads (up to 24 more). Networks that publish chains get every part; the others get the first post alone.
    
</dd>
</dl>

<dl>
<dd>

**scheduled_at:** `typing.Optional[datetime.datetime]` — When it goes out, with `status` scheduled: exact with `Z` or an offset, else a local time in `timeZone` or the profile's. Never with `queue: true`.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — Reads a `scheduledAt` without an offset; the profile's time zone when left out.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, typing.Optional[ValidatePostsRequestFieldsValue]]]` — Custom field values by key (List custom fields), such as `{ "campaign": "Winter menu" }`.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[ValidatePostsRequestStatus]` — draft (the default) never publishes. scheduled needs a future `scheduledAt`, or `queue: true`.
    
</dd>
</dl>

<dl>
<dd>

**queue:** `typing.Optional[bool]` — Schedules it at the next time of its profile's queue (`Get a profile's queue`) when none of its accounts has a post then and none would pass its network's daily cap, up to 90 days ahead. Instead of `scheduledAt`, never with it; `status` becomes scheduled, and the answer's `scheduledAt` is the time it took. A queue with no times answers `queue_empty`, one with none free `queue_full`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L517-L554">publish</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every target that is not live goes out now, failed ones included. A draft or scheduled post becomes scheduled for now; follow each target's `status` until it is `published` or `failed`. Targets whose result is `unknown` are left alone: check the network first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.publish(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L556-L593">restore</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Within 30 days of deleting it. A scheduled post whose time has passed, or with a target whose account is no longer in its profile (moved to another), comes back as a draft. A post moved to Deleted because its account was removed comes back as it was: its parts on that account (`accountRemoved`) go out only once the account is connected again. Until then they fail at their time, saying why, and scheduling or publishing the post is refused.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.restore(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L595-L632">share</a>(...) -> SharePostsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a page anyone with the link can open without signing in: the post as it will look on each of its accounts, and nothing else about it. The link works for 30 days. Sharing again makes a new link and gives every link of the post that still works 30 more days. Stopping the share or deleting the post turns them all off.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.share(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posts.<a href="src/rizamo/posts/client.py#L634-L671">unshare</a>(...) -> Post</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every preview link of the post stops working at once. `sharedUntil` becomes null.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.posts.unshare(
    id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post's id (`post_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Network posts
<details><summary><code>client.network_posts.<a href="src/rizamo/network_posts/client.py#L33-L114">list</a>(...) -> ListNetworkPostsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every post on the team's connected accounts, whoever made it: published through Rizamo (`origin` rizamo, with its `postId`) or in the network's own apps (`external`). Newest first, a page at a time: pass `nextCursor` as `cursor` for the next one. Rizamo finds new posts within the hour; when an account is connected it reads back 12 months. A LinkedIn profile's posts made outside Rizamo are not listed, as LinkedIn lists them to select developers only. Each post has its latest metrics, read 1 hour and 6 hours after it went out (TikTok's and YouTube's from 24 hours, as their numbers come a day or more late), then daily to day 90 and every 30 days after (YouTube every 28).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.network_posts.list(
    account_id="acc_01m423bp00fz39kp5pc7m42tsw",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**account_id:** `typing.Optional[str]` — Only this account's posts (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**origin:** `typing.Optional[ListNetworkPostsRequestOrigin]` — rizamo: published through Rizamo, and `postId` is that post. external: made in the network's own apps or another tool.
    
</dd>
</dl>

<dl>
<dd>

**format:** `typing.Optional[PostFormat]` — Only posts of this format.
    
</dd>
</dl>

<dl>
<dd>

**from:** `typing.Optional[datetime.datetime]` — Published at or after.
    
</dd>
</dl>

<dl>
<dd>

**to:** `typing.Optional[datetime.datetime]` — Published at or before.
    
</dd>
</dl>

<dl>
<dd>

**deleted:** `typing.Optional[ListNetworkPostsRequestDeleted]` — Posts gone from the network are left out unless asked.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 100: 50 when left out.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.network_posts.<a href="src/rizamo/network_posts/client.py#L116-L145">get</a>(...) -> NetworkPost</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One post on a network, made through Rizamo or anywhere else: its caption, link and format, the Rizamo post it went out as, whether it is still on the network, its latest numbers with when they were read, and its `details` (rates, traffic sources, viewer types, retention, viewers) where its network gives them.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.network_posts.get(
    id="npost_01m4fkyer0em9939e5rz4f89v7",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post on the network's id (`npost_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.network_posts.<a href="src/rizamo/network_posts/client.py#L147-L185">timeline</a>(...) -> NetworkPostTimeline</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

What each day added to the post's numbers, and the totals after it, from Rizamo's reads: 1 hour and 6 hours after it went out (TikTok's and YouTube's from 24 hours), then daily to day 90 and every 30 days after (YouTube every 28). A day with no point had no change. A change between two reads several days apart is one point over those days, never split, and `gaps` says why, as it does for days Rizamo could not read. Days are the profile's.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.network_posts.timeline(
    id="npost_01m4fkyer0em9939e5rz4f89v7",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post on the network's id (`npost_`).
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — The time zone the days are in: the profile's when left out.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Media
<details><summary><code>client.media.<a href="src/rizamo/media/client.py#L31-L95">create</a>(...) -> CreateMediaResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

With `contentType` and `size` (up to 4 GB), the answer says where to send the file: PUT each part, then call `complete` if there is one, and the media is `ready`. With `url`, Rizamo downloads the file and the media is ready in the answer. Media is yours until a post uses it, and then belongs to that post's profile (or to `profileId` at once): keys and people limited to some profiles reach their own media and their profiles'. Media not used by a post within 7 days is deleted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.media.create(
    content_type="video/mp4",
    size=48211334,
    alt="Pouring latte art in slow motion",
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**url:** `typing.Optional[str]` — Import: a public http or https address. Rizamo downloads the file during this call; `contentType` and `size` are then ignored.
    
</dd>
</dl>

<dl>
<dd>

**content_type:** `typing.Optional[CreateMediaRequestContentType]` — Upload: the file's type, such as image/jpeg or video/mp4, with `size`.
    
</dd>
</dl>

<dl>
<dd>

**size:** `typing.Optional[int]` — Upload: the file's bytes, up to 4 GB. With `contentType`.
    
</dd>
</dl>

<dl>
<dd>

**alt:** `typing.Optional[str]` — Describes the image for people who cannot see it.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Optional: a profile you reach, which the media joins at once. Left out, the media is yours (the person, key or agent that added it) until a post uses it, and then joins that post's profile.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.media.<a href="src/rizamo/media/client.py#L97-L126">get</a>(...) -> Media</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One image or video: `ready` once its file arrived, with its size, dimensions and length, and a link to view it that works for a few hours.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.media.get(
    id="med_01m48vn2c0emgvm8bkwtj1hayp",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The media's id (`med_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Uploads
<details><summary><code>client.uploads.<a href="src/rizamo/uploads/client.py#L29-L82">create</a>(...) -> UploadRequest</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a page to give a person. They add images or videos there, no sign-in needed, and send them. Follow `status` with Get an upload request; its `media` are ready to use on a post. The page works for 24 hours.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.uploads.create(
    note="The photos from Saturday\'s tasting",
    max_files=10,
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**note:** `typing.Optional[str]` — What you need, shown on the page: "The photos from Saturday's tasting".
    
</dd>
</dl>

<dl>
<dd>

**max_files:** `typing.Optional[int]` — How many files the person may add, up to 20: 10 when left out.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Optional: a profile you reach, which the media joins at once. Left out, the media is yours (the person, key or agent that added it) until a post uses it, and then joins that post's profile.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/rizamo/uploads/client.py#L84-L113">get</a>(...) -> UploadRequest</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Whether the person sent their files: `done` once they did, with `media` ready to put on a post. Its page's address is only in the answer that created it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.uploads.get(
    id="upr_01m4abq540fy78hvv8x8xs62tm",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The upload request's id (`upr_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Links
<details><summary><code>client.links.<a href="src/rizamo/links/client.py#L36-L97">list</a>(...) -> ListLinksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Newest first, a page at a time: pass `nextCursor` as `cursor` for the next one.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.links.list(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**source_type:** `typing.Optional[ListLinksRequestSourceType]` — Only links Rizamo made for this kind of thing.
    
</dd>
</dl>

<dl>
<dd>

**source_id:** `typing.Optional[str]` — Only links made for this comment automation or post.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 200: 100 when left out.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.links.<a href="src/rizamo/links/client.py#L99-L162">create</a>(...) -> Link</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A short address on Rizamo's link host that sends people on to `url` and counts each click, by day and country. Nothing about the person who clicks is kept: no IP address, cookie or device. Link previews (Instagram, Facebook, WhatsApp, Slack, X and others) and bots are not counted. Without `profileId`, the link is yours (the person, key or agent that made it) and people limited to some profiles do not see it. A team makes up to 1,000 links in 24 hours, and only once it has a connected account or a paid plan (403 until then).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
from rizamo.links import CreateLinksRequestUtm

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.links.create(
    url="https://cafelumen.pt/menu",
    utm=CreateLinksRequestUtm(
        source="instagram",
        medium="social",
        campaign="winter-menu",
    ),
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**url:** `str` — Where the link sends people: a public http or https address, up to 2,048 characters, without line breaks. It is kept as the URL standard writes it (`url` in the answer: the host in ASCII, the path encoded). Rizamo's own short links are refused, so a link never points at another.
    
</dd>
</dl>

<dl>
<dd>

**utm:** `typing.Optional[CreateLinksRequestUtm]` — UTM tags Rizamo adds to `url` as `utm_*` parameters, so your own analytics (Google Analytics and the like) see where visitors came from. A tag the address already has stays as it is, never overwritten; empty ones add nothing. The tagged address is what `url` shows in the answer, and it must fit in 2,048 characters too.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — A profile you reach, which the link belongs to.
    
</dd>
</dl>

<dl>
<dd>

**expires_at:** `typing.Optional[datetime.datetime]` — When it stops working, in the future. Left out, it never expires.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.links.<a href="src/rizamo/links/client.py#L164-L193">get</a>(...) -> GetLinksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One short link, with its clicks so far, per day (UTC) and per country.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.links.get(
    id="lnk_01m4b3r6g0e48txnypr2tcytdp",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The short link's id (`lnk_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.links.<a href="src/rizamo/links/client.py#L195-L224">delete</a>(...) -> DeleteLinksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

It stops working within a minute everywhere it was shared (at most 11 minutes in a place under heavy load), and its click counts are deleted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.links.delete(
    id="lnk_01m4b3r6g0e48txnypr2tcytdp",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The short link's id (`lnk_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.links.<a href="src/rizamo/links/client.py#L226-L273">update</a>(...) -> Link</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A new `url` applies to every click from now on, wherever the link was shared; it can take a minute to reach every place, at most 11 minutes in one under heavy load. `expiresAt` null makes it never expire. A new `url` needs the team to have a connected account or a paid plan, as making a link does.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
import datetime

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.links.update(
    id="lnk_01m4b3r6g0e48txnypr2tcytdp",
    expires_at=datetime.datetime.fromisoformat("2026-12-31T23:59:59+00:00"),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The short link's id (`lnk_`).
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — Where the link sends people: a public http or https address, up to 2,048 characters, without line breaks. It is kept as the URL standard writes it (`url` in the answer: the host in ASCII, the path encoded). Rizamo's own short links are refused, so a link never points at another.
    
</dd>
</dl>

<dl>
<dd>

**expires_at:** `typing.Optional[datetime.datetime]` — When it stops working, in the future. Null: it never expires.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Inbox
<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L41-L110">list</a>(...) -> ListInboxResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One thread per first comment, with the replies under it, and one per person for messages. Those with the newest messages first, 200 at a time unless `limit` says fewer: pass `nextCursor` as `cursor` for the next page, with the same filters.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**status:** `typing.Optional[ListInboxRequestStatus]` — open: still needs an answer. done: answered or closed; a new message opens it again.
    
</dd>
</dl>

<dl>
<dd>

**kind:** `typing.Optional[ListInboxRequestKind]` — comment: a first comment on a post, with the replies under it. dm: private messages with one person. mention and review: not collected yet.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**assignee_id:** `typing.Optional[str]` — Only threads handed to this teammate: their user id (`user_`), from List members.
    
</dd>
</dl>

<dl>
<dd>

**network_post_id:** `typing.Optional[str]` — Only the comments on this post (`npost_`), as List commented posts and List posts on the networks give it.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 200: 200 when left out.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before, with the same filters.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L112-L160">posts</a>(...) -> PostsInboxResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The posts on the team's accounts that have comment threads, the most recently commented first, each with its threads counted. A page at a time, 100 unless `limit` says fewer: pass `nextCursor` as `cursor` for the next one, with the same filters.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.posts(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 100: 100 when left out.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before, with the same filters.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L162-L204">get</a>(...) -> GetInboxResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Its messages oldest first: every one without `limit`; with it, the newest `limit`, and `nextCursor`, passed as `before`, gives the ones before them.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.get(
    id="thr_01m4bvs7w0fmf9g0mrdy7j6bc5",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many of the newest messages. Left out: every message.
    
</dd>
</dl>

<dl>
<dd>

**before:** `typing.Optional[str]` — `nextCursor` from the answer before: the messages older than those it gave.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L206-L255">update</a>(...) -> Thread</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Marks it done or open, read or unread, or hands it to a teammate who reaches its profile (`assigneeId`). Nothing is sent to the network.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.update(
    id="thr_01m4bvs7w0fmf9g0mrdy7j6bc5",
    status="done",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[UpdateInboxRequestStatus]` — done closes it; a new message opens it again.
    
</dd>
</dl>

<dl>
<dd>

**unread:** `typing.Optional[bool]` — True marks it unread, false read.
    
</dd>
</dl>

<dl>
<dd>

**assignee_id:** `typing.Optional[str]` — Hand it to a teammate who reaches its profile, by user id (`user_`, from List members): an agent passing it to a person. Null unassigns.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L257-L305">reply</a>(...) -> Message</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Answers as the account: publicly under the comment, or in a private message within 24 hours of the person's last one (`replyWindowEndsAt`). A Threads, LinkedIn or YouTube reply comes back `sending` and goes out within a minute: read the thread to follow it. One that failed says why in `deliveryError`; `retryOf` tries it once more, never sending it twice.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.reply(
    id="thr_01m4bvs7w0fmf9g0mrdy7j6bc5",
    text="It is, Marta! Oat, almond or soy, at no extra cost.",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**text:** `str` — The reply, as the account sends it.
    
</dd>
</dl>

<dl>
<dd>

**retry_of:** `typing.Optional[str]` — A failed reply's message id, to try it again: the same message goes out with its own text, after Rizamo looks on the network for an earlier try, so it is never sent twice. One sent or on its way by then is returned as it is, and nothing is sent.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L307-L355">mark_post_done</a>(...) -> MarkPostDoneInboxResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every comment thread on the post that is open or unread, and whose newest message is no later than `before`, becomes done and read, as Update a thread would one by one. A thread with something newer stays as it is, and a comment that arrives later opens its thread again.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
import datetime

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.mark_post_done(
    id="npost_01m4fkyer0em9939e5rz4f89v7",
    before=datetime.datetime.fromisoformat("2026-11-06T10:14:00+00:00"),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The post on the network's id (`npost_`).
    
</dd>
</dl>

<dl>
<dd>

**before:** `datetime.datetime` — The newest message you read on the post: the latest `lastMessageAt` among the threads you listed. Threads with anything newer stay open.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L357-L392">delete_comment</a>(...) -> DeleteCommentInboxResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes the comment from its network, as the account, with the replies under it, and from the thread: it no longer shows in `Get a thread`. When it is the thread's first comment (`first`), the thread goes too, and leaves every list and count. One already gone from the network counts as deleted, so a delete that failed can be asked again. Errors: 400, before any call, when it is not a comment (a message) or its network does not allow it for this comment, with why (`moderationProblem`); 422 `capability_missing` when the account's login does not allow managing comments (on Threads, until Meta approves Rizamo's access to replies); 409 when the account needs a new login or is not active, the reply is still sending, or the network refused, with its reason; 404 for a thread or comment the caller does not reach. On Threads, 422 too for the profile's own reply until Meta approves Rizamo's access to deletes.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.delete_comment(
    id="thr_01m4bvs7w0fmf9g0mrdy7j6bc5",
    message_id="msg_01m4e3wc00ecj9ez6jrr2c6eaj",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**message_id:** `str` — The comment's message id (`msg_`), from Get a thread.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L394-L433">hide_comment</a>(...) -> Message</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Hides the comment on its network, as the account, or shows it again (`hidden: false`), then records it on the message. The account's own comments are never hidden, and on Threads only first-level replies (`first`), which hide the replies under them too. Errors: 400, before any call, when it is not a comment (a message) or its network does not allow it for this comment, with why (`moderationProblem`); 422 `capability_missing` when the account's login does not allow managing comments (on Threads, until Meta approves Rizamo's access to replies); 409 when the account needs a new login or is not active, the reply is still sending, or the network refused, with its reason; 404 for a thread or comment the caller does not reach.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.hide_comment(
    id="thr_01m4bvs7w0fmf9g0mrdy7j6bc5",
    message_id="msg_01m4dbvam0e87bh8nfk28wrqne",
    hidden=True,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**message_id:** `str` — The comment's message id (`msg_`), from Get a thread.
    
</dd>
</dl>

<dl>
<dd>

**hidden:** `bool` — True hides it, false shows it again.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inbox.<a href="src/rizamo/inbox/client.py#L435-L484">like_comment</a>(...) -> Message</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Likes the comment as the Facebook or LinkedIn Page, or takes the like back (`liked: false`), then records it on the message. Comments on Facebook or LinkedIn Pages only, by others than the Page. Errors: 400, before any call, when it is not a comment (a message) or its network does not allow it for this comment, with why (`moderationProblem`); 422 `capability_missing` when the account's login does not allow managing comments (on Threads, until Meta approves Rizamo's access to replies); 409 when the account needs a new login or is not active, the reply is still sending, or the network refused, with its reason; 404 for a thread or comment the caller does not reach.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.inbox.like_comment(
    id="thr_01m4ckt980em09vyrhvr9tf4am",
    message_id="msg_01m4evxdc0fbt8xh2rc4hhptg1",
    liked=True,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The thread's id (`thr_`).
    
</dd>
</dl>

<dl>
<dd>

**message_id:** `str` — The comment's message id (`msg_`), from Get a thread.
    
</dd>
</dl>

<dl>
<dd>

**liked:** `typing.Optional[bool]` — True likes it (the default), false takes the like back.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Members
<details><summary><code>client.members.<a href="src/rizamo/members/client.py#L26-L50">list</a>() -> ListMembersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The team's people who share a profile with you, or reach every profile, with their profiles narrowed to yours: whom to assign an inbox thread to. No emails. People are invited, changed and removed by owners in the web app.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.members.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Comment automations
<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L47-L108">list</a>(...) -> ListCommentAutomationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Newest first, with their numbers so far. Every one without `limit`; with it, a page at a time: pass `nextCursor` as `cursor` for the next one, with the same filters.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.list(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `typing.Optional[str]` — Only this account's (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[ListCommentAutomationsRequestStatus]` — Paused: comments are not answered, and those that arrive meanwhile never will be.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return. Left out: every one.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before, with the same filters.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L110-L227">create</a>(...) -> CommentAutomation</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A comment that matches a keyword, on one post or on any post of an Instagram account or Facebook Page, gets a private reply with the message and its link behind a button, once per person by default. Optionally one of up to 5 public replies is posted under it afterwards, and its thread is marked done. On Instagram a follow gate can ask them to follow and reply first, with a button that replies for them. Only top-level comments from others count, made after the automation starts; Rizamo reads comments every few minutes, so answers go out within minutes. Meta takes one private reply per comment, within 7 days of it. An account sends a set number of automated messages a day at most (`dailyCap` in the numbers), paced well under Meta's limits. Not on TikTok: automations answer by private message, and TikTok does not offer its messaging API to accounts in the EEA, Switzerland or the UK, so a TikTok account is refused with that reason.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
from rizamo.comment_automations import CreateCommentAutomationsRequestMessage

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.create(
    name="Winter menu guide",
    keywords=[
        "menu",
        "guide"
    ],
    message=CreateCommentAutomationsRequestMessage(
        text="Here is our winter menu, with every drink and pastry of the season.",
        link="https://cafelumen.pt/menu",
        button="See the menu",
    ),
    public_replies=[
        "Sent it to your messages!",
        "Check your DMs!"
    ],
    mark_done=True,
    account_id="acc_01m423bp00fz39kp5pc7m42tsw",
    network_post_id="npost_01m4fkyer0em9939e5rz4f89v7",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**name:** `str` — For people: "Guide on the October reel".
    
</dd>
</dl>

<dl>
<dd>

**message:** `CreateCommentAutomationsRequestMessage` — The private reply: its text, and the link behind a button.
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `str` — The Instagram account or Facebook Page (`acc_`) whose comments it answers (not TikTok: see Create a comment automation). It cannot change.
    
</dd>
</dl>

<dl>
<dd>

**keywords:** `typing.Optional[typing.List[str]]` — Any of them triggers it, in any case and with or without accents. Empty: every comment.
    
</dd>
</dl>

<dl>
<dd>

**match:** `typing.Optional[CreateCommentAutomationsRequestMatch]` — contains: the keyword anywhere, even inside a longer word. word (the default): as a whole word or phrase. exact: the whole comment is the keyword, give or take punctuation and spaces. Always in any case and with or without accents.
    
</dd>
</dl>

<dl>
<dd>

**exclude:** `typing.Optional[typing.List[str]]` — A comment with any of these, as whole words, never triggers it.
    
</dd>
</dl>

<dl>
<dd>

**public_replies:** `typing.Optional[typing.List[str]]` — Up to 5. After the private reply goes out, one is posted under the comment, picked at random, so the replies do not all read the same.
    
</dd>
</dl>

<dl>
<dd>

**mark_done:** `typing.Optional[bool]` — Mark the comment's thread done once the private reply went out. Off when left out.
    
</dd>
</dl>

<dl>
<dd>

**follow_gate:** `typing.Optional[CreateCommentAutomationsRequestFollowGate]` — Instagram only. The private reply asks them to follow and reply, with a button that replies for them; their reply gets the message if they follow, or the reminder once.
    
</dd>
</dl>

<dl>
<dd>

**once_per_person:** `typing.Optional[bool]` — One message per person, however many times they comment. On when left out.
    
</dd>
</dl>

<dl>
<dd>

**utm:** `typing.Optional[CreateCommentAutomationsRequestUtm]` — UTM tags added to every address in the message, so your own analytics (Google Analytics and the like) see which network and automation brought each visitor; the Rizamo links send people to the tagged address. A tag left out takes its default: `source` the network (instagram or facebook), `medium` social, `campaign` the name as a slug ("Guide on the October reel" is guide-on-the-october-reel). An empty one adds none, and a tag already in an address stays as it is. Null: none. Changing the tags, or the name while the campaign is its slug, makes new links for the new addresses; the automation's link clicks add up across them. Left out on a new automation: on, with every default.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[CreateCommentAutomationsRequestStatus]` — active (the default) answers comments made from now on; paused saves it without answering.
    
</dd>
</dl>

<dl>
<dd>

**network_post_id:** `typing.Optional[str]` — One post on the network (`npost_`, from List posts on the networks). It cannot change.
    
</dd>
</dl>

<dl>
<dd>

**post_id:** `typing.Optional[str]` — Or one Rizamo post (`post_`) with a target on the account, scheduled or live: it starts once the post is live there. It cannot change.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L229-L258">get</a>(...) -> CommentAutomation</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One comment automation: its settings, whether it is armed or paused and why, and its numbers so far.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.get(
    id="cauto_01m4h40hg0f4wa1w5cfcgpjrp3",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The comment automation's id (`cauto_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L260-L291">delete</a>(...) -> DeleteCommentAutomationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

It stops at once, with its runs. Messages already sent stay in the inbox.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.delete(
    id="cauto_01m4h40hg0f4wa1w5cfcgpjrp3",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The comment automation's id (`cauto_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L293-L386">update</a>(...) -> CommentAutomation</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The account and post cannot change. Pausing stops it at once; comments made while it is paused are never answered. Resuming starts from then.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.update(
    id="cauto_01m4h40hg0f4wa1w5cfcgpjrp3",
    status="paused",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The comment automation's id (`cauto_`).
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — For people: "Guide on the October reel".
    
</dd>
</dl>

<dl>
<dd>

**keywords:** `typing.Optional[typing.List[str]]` — Any of them triggers it, in any case and with or without accents. Empty: every comment.
    
</dd>
</dl>

<dl>
<dd>

**match:** `typing.Optional[UpdateCommentAutomationsRequestMatch]` — contains: the keyword anywhere, even inside a longer word. word (the default): as a whole word or phrase. exact: the whole comment is the keyword, give or take punctuation and spaces. Always in any case and with or without accents.
    
</dd>
</dl>

<dl>
<dd>

**exclude:** `typing.Optional[typing.List[str]]` — A comment with any of these, as whole words, never triggers it.
    
</dd>
</dl>

<dl>
<dd>

**message:** `typing.Optional[UpdateCommentAutomationsRequestMessage]` — The private reply: its text, and the link behind a button.
    
</dd>
</dl>

<dl>
<dd>

**public_replies:** `typing.Optional[typing.List[str]]` — Up to 5. After the private reply goes out, one is posted under the comment, picked at random, so the replies do not all read the same.
    
</dd>
</dl>

<dl>
<dd>

**mark_done:** `typing.Optional[bool]` — Mark the comment's thread done once the private reply went out.
    
</dd>
</dl>

<dl>
<dd>

**follow_gate:** `typing.Optional[UpdateCommentAutomationsRequestFollowGate]` — Instagram only. The private reply asks them to follow and reply, with a button that replies for them; their reply gets the message if they follow, or the reminder once.
    
</dd>
</dl>

<dl>
<dd>

**once_per_person:** `typing.Optional[bool]` — One message per person for this automation, however many times they comment.
    
</dd>
</dl>

<dl>
<dd>

**utm:** `typing.Optional[UpdateCommentAutomationsRequestUtm]` — UTM tags added to every address in the message, so your own analytics (Google Analytics and the like) see which network and automation brought each visitor; the Rizamo links send people to the tagged address. A tag left out takes its default: `source` the network (instagram or facebook), `medium` social, `campaign` the name as a slug ("Guide on the October reel" is guide-on-the-october-reel). An empty one adds none, and a tag already in an address stays as it is. Null: none. Changing the tags, or the name while the campaign is its slug, makes new links for the new addresses; the automation's link clicks add up across them.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[UpdateCommentAutomationsRequestStatus]` — paused stops it at once: comments made while it is paused are never answered. active resumes it from then.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L388-L438">runs</a>(...) -> RunsCommentAutomationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

One run per matched comment, newest first, a page at a time: pass `nextCursor` as `cursor` for the next one. A run stays when its comment is deleted, but its `threadId` may then be gone from the inbox, and a private reply not sent yet is skipped (`refused`).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.runs(
    id="cauto_01m4h40hg0f4wa1w5cfcgpjrp3",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The comment automation's id (`cauto_`).
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[RunsCommentAutomationsRequestStatus]` — pending: going out within minutes. waiting: the follow gate asked and waits for their reply. sent: the message with the link went out. skipped, failed, expired: `reason` says why.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 100: 50 when left out.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.comment_automations.<a href="src/rizamo/comment_automations/client.py#L440-L484">test</a>(...) -> CommentAutomationTest</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Whether a comment with this text would trigger it, and the messages it would send, with their Rizamo links: each as its text and its button (the link, or the follow gate's reply button). Nothing is sent or recorded. Whether the person already got it, follows the account or is within Meta's windows is only known for real comments.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.comment_automations.test(
    id="cauto_01m4h40hg0f4wa1w5cfcgpjrp3",
    text="Menu please!",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The comment automation's id (`cauto_`).
    
</dd>
</dl>

<dl>
<dd>

**text:** `str` — A sample comment.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Analytics
<details><summary><code>client.analytics.<a href="src/rizamo/analytics/client.py#L33-L105">overview</a>(...) -> AnalyticsOverview</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The numbers of the team's accounts and of every post on them, made in Rizamo or anywhere else, for a period and the one before it: views, reach, engagements, the engagement rate of the posts published, posts published, followers, the accounts' own reach and accounts engaged, each day, each network, and the top posts. A period of `days` ends yesterday, the last complete day, as `to` does when left out. With `attribution` received (the default), views are each account's own views of each day, as its network counts them (its posts' gains where its days give none, and with `fields`), and reach and engagements what arrived on the posts in the period, on posts of any age, by the day it arrived; with publish, they are the numbers so far of the posts published in the period, by the day each went out. A number a network does not give is missing, never 0, and `notes` says why. Post numbers follow the days of the profile's time zone (pass `timeZone` for another); followers and the accounts' own numbers come by the network's days, matched by date (Meta's run on Pacific time, TikTok's on UTC). TikTok's days come 2 days late and YouTube's 3.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.analytics.overview(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**days:** `typing.Optional[int]` — The last this many complete days, up to yesterday in `timeZone`: today is not over, so it is left out. 30 when neither this nor `from` is given.
    
</dd>
</dl>

<dl>
<dd>

**from:** `typing.Optional[datetime.date]` — Instead of `days`: the first day, such as 2026-10-01.
    
</dd>
</dl>

<dl>
<dd>

**to:** `typing.Optional[datetime.date]` — With `from`: the last day, yesterday when left out (today when `from` is today). Up to 365 days in all.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — The time zone the days are in. Left out: the profile's with `profileId`; else the one every profile in reach shares, or UTC when they differ.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, str]]` — Only posts made in Rizamo whose custom fields have these values, for example `fields[campaign]=Winter menu`: posts made in the networks' own apps have no fields, so they are left out, and so are followers.
    
</dd>
</dl>

<dl>
<dd>

**attribution:** `typing.Optional[OverviewAnalyticsRequestAttribution]` — received (the default): what arrived in the period, on posts of any age, on the day it arrived. publish: the posts published in the period, with their numbers so far, on the day each went out.
    
</dd>
</dl>

<dl>
<dd>

**interval:** `typing.Optional[OverviewAnalyticsRequestInterval]` — How `series` groups the days: day (the default), week (ISO weeks, Monday to Sunday) or month (calendar months). A week's or month's point counts its days as `kpis` counts a period's, from `date` to `to`, and the first and last can hold fewer days. Week or month keeps a long period short.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.analytics.<a href="src/rizamo/analytics/client.py#L107-L189">posts</a>(...) -> PostsAnalyticsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every post published in the period on the team's accounts, made in Rizamo or anywhere else, deleted ones included, with its numbers so far: its lifetime totals as Rizamo last read them, every one its network gives in `metrics`, and its `details` (rates, traffic sources, viewer types, retention, viewers) where its network gives them. Sorted by views unless asked otherwise, a page at a time. Days are the profile's, and a period of `days` ends yesterday, as in Analytics overview.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.analytics.posts(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**days:** `typing.Optional[int]` — The last this many complete days, up to yesterday in `timeZone`: today is not over, so it is left out. 30 when neither this nor `from` is given.
    
</dd>
</dl>

<dl>
<dd>

**from:** `typing.Optional[datetime.date]` — Instead of `days`: the first day, such as 2026-10-01.
    
</dd>
</dl>

<dl>
<dd>

**to:** `typing.Optional[datetime.date]` — With `from`: the last day, yesterday when left out (today when `from` is today). Up to 365 days in all.
    
</dd>
</dl>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**time_zone:** `typing.Optional[str]` — The time zone the days are in. Left out: the profile's with `profileId`; else the one every profile in reach shares, or UTC when they differ.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `typing.Optional[typing.Dict[str, str]]` — Only posts made in Rizamo whose custom fields have these values, for example `fields[campaign]=Winter menu`: posts made in the networks' own apps have no fields, so they are left out, and so are followers.
    
</dd>
</dl>

<dl>
<dd>

**sort:** `typing.Optional[PostsAnalyticsRequestSort]` — What to sort by. Posts without that number (a network that does not give it, one it hides, one not read yet) come last.
    
</dd>
</dl>

<dl>
<dd>

**order:** `typing.Optional[PostsAnalyticsRequestOrder]` — desc (the default): the highest first. asc: the lowest first.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 100: 25 when left out.
    
</dd>
</dl>

<dl>
<dd>

**offset:** `typing.Optional[int]` — How many to skip: the next page starts at `offset` plus `limit`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.analytics.<a href="src/rizamo/analytics/client.py#L191-L231">audience</a>(...) -> Audience</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Each account's audience as last read: its followers, and the people who engaged with its content this month, by age, gender, country and city (LinkedIn without age or gender, and by industry, job function, seniority and company size; YouTube without city), and when its followers are active, by the hour in UTC (`activeHours`), from TikTok, for accounts with advanced access or a verified business account, and 100 followers or more. Rizamo reads it once a week for Instagram, TikTok, Threads, LinkedIn and YouTube accounts (Instagram through either login). Followers come only for accounts with 100 followers or more. Instagram gives the engaged audience only when each group has more than 100 people; TikTok, Threads and LinkedIn give none; YouTube gives no followers (`followers` is null). A YouTube channel's engaged audience is its viewers this month (last month until the 8th, as YouTube's numbers come 2 to 3 days late), counted by their views. Facebook no longer gives a Page's audience, and other networks are not read yet: their accounts come with why.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.analytics.audience(
    profile_id="prof_01m40k9k80fxd8cvng8derm7g9",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**profile_id:** `typing.Optional[str]` — Only this profile's (`prof_`): one brand or client, from List profiles. A profile you do not reach is refused as not found.
    
</dd>
</dl>

<dl>
<dd>

**account_id:** `typing.Optional[str]` — Only this account (`acc_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Billing
<details><summary><code>client.billing.<a href="src/rizamo/billing/client.py#L26-L50">get</a>() -> Billing</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Billed per connected account, the first 2 free. Only keys and people that reach every profile see it, since the plan counts every profile's accounts.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.billing.get()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Events
<details><summary><code>client.events.<a href="src/rizamo/events/client.py#L30-L96">list</a>(...) -> ListEventsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Every change on the team's posts and accounts in the last 30 days, newest first, with who made it: a person, an API key, an agent, or Rizamo itself; and the inbox's comments and messages as they arrive, the replies sent from Rizamo, and what comment automations do. The same events webhooks send, each as one item of this list. A page at a time: pass `nextCursor` as `cursor` for the next one. Someone limited to some profiles sees only those profiles' events. The inbox's and comment automations' events carry what people wrote: a key or agent reads them only with `inbox:read` (`comment.received`, `message.received`, `message.sent`) or `automations:read` (`comment_automation.*`) too; asking for one of those types without it answers 403.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.events.list(
    resource_id="post_01m47bjzm0edmtk7w6gp7br39v",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**type:** `typing.Optional[EventType]` — Only events of this type.
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `typing.Optional[str]` — Only events about this post, account, inbox thread or comment automation. An account's include what happened on it to posts' targets (`post.target.*`), and its inbox's and automations' events.
    
</dd>
</dl>

<dl>
<dd>

**since:** `typing.Optional[datetime.datetime]` — Only events at or after this moment, within the last 30 days.
    
</dd>
</dl>

<dl>
<dd>

**until:** `typing.Optional[datetime.datetime]` — Only events before this moment.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 200: 50 when left out.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Webhooks
<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L40-L64">list</a>() -> ListWebhooksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The team's endpoints, oldest first, without their signing secrets. An owner sees every one, also through their agent or their API key; anyone else only those that send for them (`onBehalfOf`). Someone limited to some profiles sees only endpoints limited to those profiles.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.list()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L66-L124">create</a>(...) -> WebhookSecret</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Events from now on go to it, of the profiles the person it sends for reaches (`onBehalfOf`: the caller, or the person behind the API key or agent), and it is deleted when they leave the team. Each event goes as one POST of JSON (the event as `List events` gives it), signed with Standard Webhooks' headers (`webhook-id`, the event's id; `webhook-timestamp`; `webhook-signature`). A 2xx answer within 15 seconds is delivered; anything else is tried again 6 times over about 18 hours, and a 410 Gone disables the endpoint. After 10 failures in a row an endpoint's deliveries wait while one at a time tries it, and one that keeps failing like that with nothing delivered for 5 days is disabled; Rizamo emails the team's owners and the person it sends for. Never sent to rizamo.com or workers.dev addresses, nor to private ones. Deliveries are not in order: order one resource's events by `at`. Its signing secret is in the answer, and only there. A team has up to 20 endpoints.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.create(
    url="https://hooks.cafelumen.pt/rizamo",
    description="Posts to our CRM",
    events=[
        "post.published",
        "post.failed",
        "post.target.failed"
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**url:** `str` — Where Rizamo sends events: an https address on the public internet.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — What it is for, for the people of the team.
    
</dd>
</dl>

<dl>
<dd>

**events:** `typing.Optional[typing.List[WebhookEventType]]` — The event types it receives. Null: every type, those Rizamo adds later included. A key or agent lists the inbox's types (`comment.received`, `message.received`, `message.sent`) only with `inbox:read`, and `comment_automation.*` only with `automations:read`; with null, the endpoint gets none of those it cannot read.
    
</dd>
</dl>

<dl>
<dd>

**profile_ids:** `typing.Optional[typing.List[str]]` — Only events of these profiles. Null: every profile's, and the events of no profile. Someone limited to some profiles gives some of theirs.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L126-L155">delete</a>(...) -> DeleteWebhooksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Nothing more is sent to it, and its deliveries are deleted with it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.delete(
    id="wh_01m4m44q00ea9a11gpjs99ddcy",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook endpoint's id (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L157-L219">update</a>(...) -> WebhookEndpoint</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Changes apply to events from now on, and to deliveries still waiting for a retry: each is checked against the endpoint as it is when its turn comes. A delivery whose event the endpoint no longer takes (its new types or profiles) ends unsent, with `endpoint_changed` on its attempt; the ones it still takes go to its new `url`. A new `url` starts with a closed breaker, makes the caller (or the person behind the API key or agent) the person it sends for (so does any change to one that sends for nobody, `onBehalfOf` null), and the deliveries it had already tried or held at the old address end with `endpoint_changed` (replay them to send them to the new one). `enabled` false stops it, and its waiting deliveries end at once with `endpoint_disabled`; true starts it again for new events, also after a 410 Gone or days of failures, with its failures forgotten. What ended while it was off is not sent by itself: replay it (`Replay an endpoint's deliveries`).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.update(
    id="wh_01m4m44q00ea9a11gpjs99ddcy",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook endpoint's id (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — Where Rizamo sends events: an https address on the public internet.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — What it is for, for the people of the team.
    
</dd>
</dl>

<dl>
<dd>

**events:** `typing.Optional[typing.List[WebhookEventType]]` — The event types it receives. Null: every type, those Rizamo adds later included. A key or agent lists the inbox's types (`comment.received`, `message.received`, `message.sent`) only with `inbox:read`, and `comment_automation.*` only with `automations:read`; with null, the endpoint gets none of those it cannot read.
    
</dd>
</dl>

<dl>
<dd>

**profile_ids:** `typing.Optional[typing.List[str]]` — Only events of these profiles. Null: every profile's, and the events of no profile. Someone limited to some profiles gives some of theirs.
    
</dd>
</dl>

<dl>
<dd>

**enabled:** `typing.Optional[bool]` — false stops it; true starts it again, also after a 410 Gone or days of failures.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L221-L258">rotate_secret</a>(...) -> WebhookSecret</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A new signing secret, in the answer and only there. For 24 hours each delivery carries two signatures in `webhook-signature`, one with each secret, so the receiver can switch without losing any; then only the new one.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.rotate_secret(
    id="wh_01m4m44q00ea9a11gpjs99ddcy",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook endpoint's id (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L260-L297">test</a>(...) -> WebhookDelivery</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

A delivery of type `webhook.test` sent now, signed as every delivery is, and its attempt in the answer. It is tried once, never retried, and shows in the deliveries. A disabled endpoint can be tested. A team sends up to 10 tests a minute; more answer 429.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.test(
    id="wh_01m4m44q00ea9a11gpjs99ddcy",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook endpoint's id (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L299-L351">deliveries</a>(...) -> DeliveriesWebhooksResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Each event (and test) sent to an endpoint, newest first, with every attempt, from the last 30 days. A page at a time: pass `nextCursor` as `cursor` for the next one. Only deliveries of endpoints the caller sees; someone limited to some profiles sees only their profiles' events among them, and tests. Each payload is an event as `List events` shows it, so `webhooks:read` reads what `events:read` reads: the inbox's and comment automations' deliveries only with `inbox:read` or `automations:read` too.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.deliveries(
    endpoint_id="wh_01m4m44q00ea9a11gpjs99ddcy",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**endpoint_id:** `typing.Optional[str]` — Only deliveries to this endpoint (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[DeliveriesWebhooksRequestStatus]` — pending: not tried yet. retrying: tried, and tried again at `nextAttemptAt`. delivered: an attempt got a 2xx. failed: Rizamo stopped trying (all retries used, a 410, an address it does not send to, the endpoint disabled or no longer taking the event, or a delivery it could not prepare).
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — How many to return, up to 100: 50 when left out.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the page before.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L353-L390">replay</a>(...) -> WebhookDelivery</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends a delivery again, once and now, through the queue: the body it sent before (made from its event when it never went), signed anew, with the same `webhook-id` (the event's id), so a receiver that has it already can skip it. One more attempt, to the endpoint's `url` as it is now, never retried; it shows among the delivery's attempts. The endpoint must still take the event (its types and profiles now) and be enabled. A delivery still waiting for a retry is refused: it goes on its own. A team replays up to 5,000 deliveries an hour, one at a time and by range together; more answer 429.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.replay(
    id="whd_01m4mw5rc0ehs83dnfzc56pd0g",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook delivery's id (`whd_`).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.webhooks.<a href="src/rizamo/webhooks/client.py#L392-L458">replay_range</a>(...) -> WebhookReplay</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends again, once each and now, the endpoint's deliveries made between `since` and `until` (within the last 30 days): the failed ones, or every one with `status` all. Each keeps its `webhook-id` and goes to the endpoint's `url` as it is now. Deliveries the endpoint no longer takes are skipped, and those still waiting for a retry are not replayed. Up to 1,000 a call, in the order they were made, and within the team's 5,000 replays an hour (429 once none are left); `more` says the range holds more, and `nextCursor` continues after the last one this call looked at. One range at a time: a call while the endpoint's last replay is still being sent answers 409. The endpoint must be enabled.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from rizamo import Rizamo
from rizamo.environment import RizamoEnvironment
import datetime

client = Rizamo(
    api_key="<token>",
    environment=RizamoEnvironment.PRODUCTION,
)

client.webhooks.replay_range(
    id="wh_01m4m44q00ea9a11gpjs99ddcy",
    since=datetime.datetime.fromisoformat("2026-11-06T00:00:00+00:00"),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `str` — The webhook endpoint's id (`wh_`).
    
</dd>
</dl>

<dl>
<dd>

**since:** `datetime.datetime` — From this moment, included.
    
</dd>
</dl>

<dl>
<dd>

**until:** `typing.Optional[datetime.datetime]` — To this moment, excluded. Now when left out.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[ReplayRangeWebhooksRequestStatus]` — failed (the default): only deliveries that did not arrive. all: delivered ones too.
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — `nextCursor` from the call before, with the same range: continues after the last delivery it looked at.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

