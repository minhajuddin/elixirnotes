# Ecto model with a UUID primary key

~~~elixir
# model
defmodule Simpleform.Form do
  use Simpleform.Web, :model

  @primary_key {:id, :binary_id, autogenerate: true }

  schema "forms" do
    field :name, :string

    timestamps
  end

  # ...

end
~~~

~~~elixir
# migration
defmodule Simpleform.Repo.Migrations.CreateForm do
  use Ecto.Migration

  def change do
    create table(:forms, primary_key: false) do
      add :id, :uuid, primary_key: true
      add :name, :string

      timestamps
    end

  end
end
~~~
